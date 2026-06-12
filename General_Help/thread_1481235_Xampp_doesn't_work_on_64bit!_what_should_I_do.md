---
title: "Xampp doesn't work on 64bit! what should I do?"
date: 2010-05-12
forum: General Help
---

### Post by ibrahim.k on 2010-05-12
Hi,

I have installed Lucid Lynx 10.04.

and Xampp doesn't work work on it because it is a 64bit architecture.

IS there an equivalent ? 

thnx

---

### Post by ibrahim.k on 2010-05-15
Everything is okay now,
I have installed these packages using "synaptick package manager"
Apache2
phpmyadmin
mysql-server5.1
all of these services will start automatically once you finish installing it.
and if you want to start,stop, restart. the apache service
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
or
sudo /etc/init.d/apache2 restart

if you want to use a graphical interface instead of terminal 
you can download webmin

[http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.510-2_all.deb)

---

