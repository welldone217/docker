
FROM python:3.6.1-slim

WORKDIR /var/www/django

RUN echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib" > /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian/ jessie-updates main non-free contrib" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib" >> /etc/apt/sources.list && \
   apt-get update && apt-get install -y --no-install-recommends \
      gcc  \
      gettext libpcre3 libpcre3-dev\
      mysql-client libmysqlclient-dev  \
      &&  rm -rf /var/lib/apt/lists/* \
      &&  rm -rf /tmp/*
       
Run   pip3 install django \
  &&  pip3 install mysqlclient  \
  &&  pip3 install uwsgi \
  &&  pip3 install virtualenv \
  &&  pip3 install rsa \
  &&  pip3 install django-simple-captcha \
  &&  pip3 install whitenoise \
  &&  virtualenv -p /usr/local/bin/python3 virtualenvs
   
COPY uwsgi.ini /var/www/django/
EXPOSE 8001 
CMD ["uwsgi","--ini","/var/www/django/uwsgi.ini"]
