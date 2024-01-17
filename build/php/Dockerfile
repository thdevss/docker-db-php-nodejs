FROM php:8.2-fpm-alpine
ADD ./build/php/www.conf /usr/local/etc/php-fpm.d/www.conf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD ./app/www /var/www/html

WORKDIR /var/www/html
RUN composer install --no-interaction --optimize-autoloader

RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN ln -s /var/www/html/storage/app/public/ /var/www/html/public/storage

EXPOSE 80
CMD ["php-fpm"]