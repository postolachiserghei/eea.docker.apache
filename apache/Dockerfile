FROM centos:centos6
MAINTAINER "Vitalie Maldur" <vitalie.maldur@eaudeweb.ro>
MAINTAINER "Alin Voinea" <alin.voinea@eaudeweb.ro>

ENV UID 1000
ENV USER apache

RUN groupadd -g $UID $USER; useradd -u $UID -g $UID -m -s /bin/bash $USER
RUN yum -y update; \
    yum -y install httpd mod_ldap mod_session mod_ssl; \
    yum clean all

RUN chown -R $UID:$UID /var/www

EXPOSE 80

ADD src/run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]
