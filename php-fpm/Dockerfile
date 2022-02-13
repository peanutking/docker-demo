FROM php:7.3-fpm

EXPOSE 9000
EXPOSE 8008

COPY php.ini /usr/local/etc/php/
COPY www.conf /usr/local/etc/php-fpm.d/
COPY html/ /usr/share/nginx/html/

RUN docker-php-ext-install mysqli pdo pdo_mysql bcmath
RUN pecl install -o -f redis \
&&  rm -rf /tmp/pear \
&& docker-php-ext-enable redis

RUN apt-get update -y
RUN apt-get install -y libgmp-dev
RUN ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/local/include/
RUN docker-php-ext-configure gmp
RUN docker-php-ext-install gmp