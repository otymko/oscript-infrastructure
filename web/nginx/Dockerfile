#FROM jwilder/nginx-proxy
FROM ubuntu:16.04

COPY cat_me_to_fastcgi_params /tmp/

RUN apt-get update && apt-get -y install nginx
RUN cat /tmp/cat_me_to_fastcgi_params >> /etc/nginx/fastcgi_params && rm /tmp/cat_me_to_fastcgi_params

COPY ssl_conf /etc/nginx/ssl_conf
COPY sites-enabled /etc/nginx/sites-enabled
RUN rm /etc/nginx/sites-enabled/default

# FIXME
# volume перекрывает весь контент, лежащий в образе
# сейчас сайт веб-документации помещается в контейнер nginx руками через docker cp

VOLUME /var/www

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
