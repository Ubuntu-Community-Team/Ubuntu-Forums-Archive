---
title: "How to enable Nginx PHP services (php-cgi) in Ubuntu"
date: 2010-04-11
forum: General Help
---

### Post by docplastic on 2010-04-11
# This procedure explains how to enable Nginx PHP services (php-cgi) in Ubuntu (>=9.10), by using a simple upstart file to start and keep up php-cgi support (runing in external FASTCGI Mode).

**# Tested on Ubuntu 9.10**

**## Install PHP**
# Ubuntu 9.10: PHP 5.2.10-2ubuntu6.4
sudo aptitude -R install php5-cgi php5-mysql php5-imap php5-mcrypt php5-gd # php5-gd is usually needed

# security tip: hide php version
sudo sed -i '/expose_php/s/\;exp/exp/;/expose_php/s/=.*/= 0/' /etc/php5/cgi/php.ini
grep 'expose_php' /etc/php5/cgi/php.ini

# We use Ubuntu's Upstart system to keep php-cgi support up.
# If you do not want to use Ubuntu's upstart system see bellow,
# the alternative (init.d) php-cgi upstart file

# Note: using Linux socket binding, instead of the IP binding,
#           will improve server performance:
# /usr/bin/php-cgi -q -b /tmp/php-fastcgi.socket # socket binding
# But if you want to use the less elegant "fastcgi_pass 127.0.0.1:9000;" in your nginx conf files, you must replace "/tmp/php-fastcgi.socket" for "127.0.0.1:9000" in the following upstart script
# /usr/bin/php-cgi -q -b 127.0.0.1:9000 # IP binding-> IP:port

**## create a php-cgi upstart file**
# You may learn more about upstart at: [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)
#
sudo tee /etc/init/php-fastcgi.conf <<-\EOA
# /etc/init/php-fastcgi.conf
# php-fastcgi - starts php-cgi as an external FASTCGI process
description "php-fastcgi - keep up php-fastcgi"
start on runlevel [2345]
stop on runlevel [!2345]
respawn
exec /usr/bin/sudo -u www-data PHP_FCGI_CHILDREN=5 PHP_FCGI_MAX_REQUESTS=125 /usr/bin/php-cgi -q -b /tmp/php-fastcgi.socket
EOA

**# start the php-fastcgi service**
sudo /sbin/start php-fastcgi # start

**# check status**
sudo /sbin/status php-fastcgi
ps -ef | sed '/!d/d;/cgi/!d' # ps cuxa | sed '/!d/d;/cgi/!d'

# security tip: enable suhosin security hardening
# Suhosin will work out of the box with its default configuration
# <[http://www.hardened-php.net/suhosin/configuration.html](http://www.hardened-php.net/suhosin/configuration.html)>
sudo aptitude install php5-suhosin

# restart php-fastcgi processes
#pgrep php-cgi;echo;sudo pkill php-cgi;sleep 1; pgrep php-cgi

# stop php-fastcgi
#sudo /sbin/stop php-fastcgi && sudo rm /tmp/php-fastcgi.socket

**## change nginx config files**
# change the relevant files in /etc/nginx/sites-available/*
# check lines after: '# pass the PHP scripts to FastCGI server'
# sudo nano /etc/nginx/sites-available/default
	location ~ \.php$ {
		include /etc/nginx/fastcgi_params;
		fastcgi_pass unix:/tmp/php-fastcgi.socket;
		#fastcgi_pass 127.0.0.1:9000;
		fastcgi_index index.php;
		fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
	}

## END OF PROCEDURE ##

---

