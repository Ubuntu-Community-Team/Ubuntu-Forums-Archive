---
title: "Can not Apache to load php file"
date: 2010-06-29
forum: General Help
---

### Post by walterbyrd on 2010-06-29
I am using Ubuntu 10.04. This is my desktop PC. 

When I installed Apache, I kept getting the message:

> 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


Apache will run a php file from the /var/wwww/ directory just fine. But, Apache will not run a php file from a subdirectory of the /var/www/  directory. Permissions are set wide open. 

When I try to run a php file from a subdirectory I get an option to save the file, or browse the file.

---

### Post by jeicrash on 2010-06-29
You may have not installed php completely or at all.
Try installing php5 and libapache2-mod-php5

sudo apt-get install php5 libapache2-mod-php5

Apache will need restarted afterwards


sudo /etc/init.d/apache2 restart


Please let us know if this does not fix the problem.

Jei

---

### Post by walterbyrd on 2010-06-29
Thank you for the fast reply. But, that did not fix the problem. 

It looks at though php was installed.

---

### Post by gvernold on 2010-06-29
I have exactly the same problem. I found some information in another thread about changing something in the php.conf file in modules-enabled and the file is not there. In fact I searched my entire system and still cannot find a php.conf file. I have reinstalled Apache and PHP twice over, restarted the machine and Apache in between and still cannot view a web page with php, instead Firefox just offers to open in at an ordinary file.

Synaptic shows all the PHP libraries installed properly but I cannot open a single .php page. Just for the record I tried opening it in Opera too but that doesn't work either.

Any advice would be much appreciated.

---

### Post by walterbyrd on 2010-06-29
The php conf file may be one of these:

> 
# ls -l /usr/bin/php*
lrwxrwxrwx 1 root root      21 2010-05-12 13:03 /usr/bin/php -> /etc/alternatives/php
-rwxr-xr-x 1 root root 7454868 2010-05-13 14:16 /usr/bin/php5
-rwxr-xr-x 1 root root 7446608 2010-05-13 14:16 /usr/bin/php5-cgi
lrwxrwxrwx 1 root root      25 2010-06-29 11:03 /usr/bin/php-cgi -> /etc/alternatives/php-cgi



Or the file may be: /etc/php5/cgi/php.ini
Or maybe /etc/php5/apache2/php.ini

I also found a /etc/apache2/mods-enabled/php5.conf file.

---

### Post by gvernold on 2010-06-29
not in any of those I'm afraid. I'm just looking for the link I had about the solution which might actually help you out. Just wish I had a php.conf I could change.

---

### Post by gvernold on 2010-06-30
Alright, found the link:

[http://www.jeremykendall.net/2010/04/30/upgrading-to-ubuntu-10-04-breaks-serving-php-from-home-directories/](http://www.jeremykendall.net/2010/04/30/upgrading-to-ubuntu-10-04-breaks-serving-php-from-home-directories/)

I still don't have a php.conf file and nowhere to configure it but all the required apps (libapache2 etc) are installed and have been reinstalled three times. Looks like I'm going to have to reinstall my entire system because of this.

---

### Post by jeicrash on 2010-06-30
If you do not have a php.conf you may have to make the changes in php.ini mine is located /etc/php5/apache2/php.ini

I did not find any php.conf file on my system either but have several working php files.

---

