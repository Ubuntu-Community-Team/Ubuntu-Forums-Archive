---
title: "problems installing Apache2, phpmyadmin Ubuntu 10.04"
date: 2011-11-03
forum: General Help
---

### Post by skeptical4life on 2011-11-03
Ubuntu 10.04; i386pc
I'm relatively new to Ubuntu and have spent days trying to install a local host so I can work on my Joomla 1.7.2 site (that I created in Windows) and have had several problems.
1. phpMyadmin isn't showing in www folder
2. Permissions issues re: phpMyadmin and mysql
3. When following install instructions <[http://www.youtube.com/watch?v=-mG8kgMHK2A](http://www.youtube.com/watch?v=-mG8kgMHK2A) > I get this error:
:~$ sudo apt-get install linapache2-mod-auth-mysql phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linapache2-mod-auth-mysql


More Info reported:
PHP Version 5.3.5-1ubuntu7.3

System 	Linux michael-Gateway-M520 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686
Build Date 	Oct 13 2011 21:55:18
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
Additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/imap.ini, /etc/php5/apache2/conf.d/mcrypt.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/suhosin.ini
PHP API 	20090626
PHP Extension 	20090626
Zend Extension 	220090626
Zend Extension Build 	API220090626,NTS
PHP Extension Build 	API20090626,NTS
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
Zend Multibyte Support 	disabled
IPv6 Support 	enabled
Registered PHP Streams 	https, ftps, compress.zlib, compress.bzip2, php, file, glob, data, http, ftp, phar, zip
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	zlib.*, bzip2.*, convert.iconv.*, string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, dechunk, mcrypt.*, mdecrypt.*


What should I do?

---

