---
title: "phpmyadmin  html file missing"
date: 2011-03-19
forum: General Help
---

### Post by spindler on 2011-03-19
I am setting up a new install of Ubuntu 10.10 with a lamp.

I configured mysql with a temporary database and installed phpmyadmin

sudo apt-get install phpmyadmin

Everything seamed to install ok however I cannot see the phpmyadmin when i go tot eh following address.

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

When I check the error log it tells me there is no file available called phpmyadmin.php

When I look in the directory  /var/www/   indeed there is no file.

So where did it go?    How do I get this file in the right location?  Why did it not get installed?  How do I fix this.

I attempted to remove phpmyadmin and re-install the program however this does not solve my problem  i am doing the following

sudo apt-get remove phpmyadmin
sudo apt-get install phpmyadmin

---

### Post by WorMzy on 2011-03-19
See if this helps you: [https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

### Post by spindler on 2011-03-19
Ok.... I just attempted to follow the instructions.  I got through most of it until I get an error about the phpinfo.php file.   It says it is still open although it is not.  In fact when I attempt to look at the phpinfo.php file I cannot open it now.

Any ideas?   

Here is the command line report.

$ sudo gedit apache2.conf
$ sudo dpkg-reconfigure -plow phpmyadmin
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
$ sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
$ sudo /etc/init.d/apache2 reload
apache2: Syntax error on line 230 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/sites-enabled/phpinfo.php: /etc/apache2/sites-enabled/phpinfo.php:1: <?> was not closed.
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
:/etc/apache2$ sudo /etc/init.d/apache2 reload
apache2: Syntax error on line 230 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/sites-enabled/phpinfo.php: /etc/apache2/sites-enabled/phpinfo.php:1: <?> was not closed.
Action 'configtest' failed.
The Apache error log may have more information.

---

