# PHP Version
FROM php:7.4.30-fpm

# Install the PHP extensions we need
RUN apt-get update && \
apt-get install -y --no-install-recommends \
    curl \
    git \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libicu-dev \
    libssl-dev \
    libmcrypt-dev && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd mysqli opcache intl

 # INSTALL memcached
RUN apt-get update
RUN apt-get install -y git libmemcached-dev wget unzip
RUN apt-get install --no-install-recommends -y libzip-dev 
RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip

RUN mkdir -p /usr/src/php/ext/memcached
WORKDIR /usr/src/php/ext/memcached
RUN wget https://github.com/php-memcached-dev/php-memcached/archive/v3.1.3.zip; unzip /usr/src/php/ext/memcached/v3.1.3.zip
RUN mv /usr/src/php/ext/memcached/php-memcached-3.1.3/* /usr/src/php/ext/memcached/

RUN docker-php-ext-configure memcached && docker-php-ext-install memcached 