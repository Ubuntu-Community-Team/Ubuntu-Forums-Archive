---
title: "virtual hosting stopped working"
date: 2011-04-08
forum: General Help
---

### Post by daverx on 2011-04-08
I run ubuntu 10.10 with apache2 and have 2 virtual hosts set up

here is an example of one of the virtual hosts

<VirtualHost *:80>
  ServerName blah.endofinternet.org
  ServerAlias blah.endofinternet.org
  ServerAdmin [email]davidboychuck@gmail.com[/email]
  DocumentRoot /var/www/blah

  <Directory /var/www/blah/>
    Options -Indexes FollowSymLinks MultiViews
    AllowOverride none
    Order allow,deny
    allow from all
  </Directory>

</VirtualHost>

Everything was working perfectly until i changed the internal ip of my router from 192.168.1 to 192.168.192 and now virtual hosting no longer works. As far as I can tell everything is setup correctly.

From the apache error log:

[Sun Apr 03 16:41:50 2011] [error] [client 66.249.72.208] script '/var/www/index.php' not found or unable to stat
[Sun Apr 03 22:49:42 2011] [error] [client 66.249.72.208] script '/var/www/index.php' not found or unable to stat
[Mon Apr 04 00:26:48 2011] [error] [client 88.80.10.1] File does not exist: /var/www/pp
[Mon Apr 04 04:57:58 2011] [error] [client 66.249.72.208] File does not exist: /var/www/robots.txt
[Mon Apr 04 04:57:58 2011] [error] [client 66.249.72.208] script '/var/www/index.php' not found or unable to stat

It looks like it's just not trying to use the vhost document root because when i go to blah.endofinternet.org it just takes me to the default site.

Not sure what to do or where to look for a problem. Any help is appreciated.

---

