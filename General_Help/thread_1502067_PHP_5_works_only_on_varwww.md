---
title: "PHP 5 works only on /var/www"
date: 2010-06-05
forum: General Help
---

### Post by leetkrew on 2010-06-05
hello there,

i am having a problem while configuring my web server. 

PHP 5 works on /var/www but apache is sending me my source codes if uploaded in home directories.
/home/user1/public_html/test.php
/home/user2/public_html/test.php



I have a working phpmyadmin ([http://server/phpmyadmin](http://server/phpmyadmin)) 


------------

Things that i have done:
1) apt-get install libapache2-mod-php5 php5-cli php5-common php5-cgi
2) sudo a2enmod ssl, sudo a2enmod rewrite, sudo a2enmod suexec, sudo a2enmod include
3) ~# whereis php ---> /usr/bin/php 
4) a2enmod php5, a2enmod userdir
5) Added php on mime.conf ( application/x-httpd-php .php )
6) Include /etc/phpmyadmin/apache.conf, Include /etc/apache2/mods-enabled/*.load, Include /etc/apache2/mods-enabled/*.conf, Include /etc/apache2/httpd.conf
7) httpd.conf file

```
<VirtualHost MY.WAN.IP.ADDRESS:80>
	DocumentRoot /home/user1/public_html/
	ServerName site1.com
	ServerAlias www.site1.com
	ServerAlias site1.local
	ErrorLog /home/user1/logs/error.log
	<Directory "/home/user1/public_html/">
		Options Indexes FollowSymLinks MultiViews Includes ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>
```
8) cleared browser cache
9) /etc/init.d/apache2 restart

I am using ubuntu server without GUI


please help. thanks :)

---

### Post by leetkrew on 2010-06-05
EDIT: 


I solved the problem by viewing each configuration file. 


Modify php5.conf and restart apache
```
sudo nano /etc/apache2/mods-enabled/php5.conf
sudo /etc/init.d/apache2 restart

```

---

### Post by .:PiXi²:. on 2010-06-05
So you may now mark this thread as solved...

---

### Post by mirakus on 2010-12-15
Leetkrew,

Could you elaborate on exactly what you did to solve this problem?  I am having (seemingly) the exact same issue on Debian Lenny.  PHP is parsed and working in /var/www, but if I try to pull up any page that is in a subdirectory of /var/www, it doesn't work and attempts to download the file.  I recall having it set up and working like that on a different computer before, so I'm not sure what the issue is now.

---

