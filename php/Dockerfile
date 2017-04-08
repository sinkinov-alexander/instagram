FROM php:fpm

RUN apt-get update 

RUN apt-get install -y \
    git libmemcached-dev 

RUN apt-get install libmcrypt-dev -y \
	&& docker-php-ext-install -j$(nproc) mcrypt

RUN docker-php-ext-install -j$(nproc) pdo_mysql

RUN mkdir /code && chown -R www-data /code

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN pecl install redis && docker-php-ext-enable redis

WORKDIR /code

CMD ["php-fpm"]