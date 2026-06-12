---
title: "apache error"
date: 2009-10-14
forum: General Help
---

### Post by r_s on 2009-10-14
I installed apache on my ubuntu 9.04 but when I start it and use the command
sudo /etc/init.d/apache2 start ...It shows me an error which is like this 
.: 44: Can't open /etc/apache2/envvars
Please help .

---

### Post by Switch08 on 2009-10-14
[http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/](http://dancingpenguinsoflight.com/2009/02/how-to-completely-reset-an-apache-instance-in-ubuntu/)


44: Can't open /etc/apache2/envvars

sudo dpkg --get-selections | grep apache
sudo apt-get remove --purge apache2 apache2-mpm-worker apache2-threaded-dev apache2-utils apache2.2-common libapache2-mod-python libapache2-mod-python-doc libapache2-mod-wsgi

sudo apt-get install apache2 libapache2-mod-python libapache2-mod-wsgi libapache2-mod-python-doc

Did you google at all?

---

