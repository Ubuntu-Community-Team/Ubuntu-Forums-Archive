---
title: "Web server losing connection to outside world"
date: 2009-10-21
forum: General Help
---

### Post by JBauer5 on 2009-10-21
I have a web server that is failing to connect outside the network every so often.  If you go to to the website on the network it's fine, but outside it doesn't connect.

I'm thinking it might have something to do with the backup program I installed recently.

I'm telling it to backup:
/etc/apache2
/var/www
/etc/mysql
/usr/share/mysql
/usr/bin/mysql

Am I accidentally backing up any working directories or something?  Or should I consider the problem unrelated?

---

### Post by kushal.kumaran on 2009-10-25
It doesn't seem like the backup could do any harm, even if you did backup any working directories, since it probably doesn't write to any of them.  You might have to do some network debugging to check if the connection requests from outside your network are reaching the web server.  Do any requests show up in the access logs (/var/log/apache2/access.log)?

You should also probably know that in the default setup of the mysql server package, the data directory is /var/lib/mysql and that backing up mysql data from a running database requires some care.  The mysql manual has details.

---

