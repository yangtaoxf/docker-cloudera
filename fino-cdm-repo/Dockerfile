########################################################################
# bind local port 24500
#########################################################################
FROM fino-cdm-envbase:v2.0
MAINTAINER linzhihuang 
RUN apt-get -y install apache2
RUN mkdir -p /data/soft/pool /data/soft/dist /data/soft/cloudera /var/log/apache2
COPY ./debfiles/* /data/soft/pool/
COPY clouderasources/* /data/soft/cloudera/
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
RUN cd /data && dpkg-scanpackages soft/pool | gzip > soft/Packages.gz
RUN cd /var/www/html && ln -s /data
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]

