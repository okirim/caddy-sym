FROM php:8.1-fpm


#install caddy
RUN apt update \
    && apt install -y debian-keyring debian-archive-keyring apt-transport-https \
    && curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg \
    && curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | tee /etc/apt/sources.list.d/caddy-stable.list \
    && apt update \
    && apt install caddy
#set up app


COPY .docker/Caddyfile /etc/caddy/Caddyfile
COPY . /var/www
WORKDIR /var/www

RUN apt install vim -y

RUN chown -R www-data:www-data /var/www

#RUN caddy file-server --domain localhost

#CMD ["caddy","start", "--config", "/etc/caddy/Caddyfile"]

