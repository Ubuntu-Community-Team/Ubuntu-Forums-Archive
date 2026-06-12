---
title: "PHP5 GD Library not working"
date: 2011-11-25
forum: General Help
---

### Post by vbSteve on 2011-11-25
Hi,


I have a PHP website running on my apache server and I'm having troubles setting up the GD library.

For some reason I can't get it to work.

On the website, I get the following fatal error:
Fatal error: Call to undefined function imagecreatefromjpeg() in /home/webmaster/www/Test/lib/functions.php on line 159

The most likely cause of this error is that GD is not installed, so I ran these commands:

# apt-get update
# apt-get install php5-gd
# /etc/init.d/apache2 restart

It should work, but I still get the error on my site. I've also tried restarting the server with no result.

This is my configuration:

```


$ php5 -m |grep gd
gd


$ cat /etc/php5/apache2/php.ini |grep gd
[gd]
; a gd image. The warning will then be displayed as notices
; http://php.net/gd.jpeg-ignore-warning
;gd.jpeg_ignore_warning = 0


$ cat /etc/php5/apache2/conf.d/gd.ini
; configuration for php GD module
extension=gd.so


PHPINFO
System:	Linux odessey-server 2.6.35-31-generic-pae #62-Ubuntu SMP Tue Nov 8 15:43:23 UTC 2011 i686
Build Date: Oct 14 2011 22:31:21
Server API: Apache 2.0 Handler
Virtual Directory Support: disabled
Configuration File (php.ini) Path: /etc/php5/apache2
Loaded Configuration File: /etc/php5/apache2/php.ini
Scan this dir for additional .ini files: /etc/php5/apache2/conf.d
Additional .ini files parsed: 
 /etc/php5/apache2/conf.d/gd.ini, 
 /etc/php5/apache2/conf.d/mcrypt.ini, 
 /etc/php5/apache2/conf.d/mysql.ini, 
 /etc/php5/apache2/conf.d/mysqli.ini, 
 /etc/php5/apache2/conf.d/pdo.ini, 
 /etc/php5/apache2/conf.d/pdo_mysql.ini

```

I've been troubleshooting for hours now and I can't find anything.
Anyone has some more information about this problem? 

Thanks,
Steve

---

### Post by NaitoNeko on 2012-08-14
How did you solved it ?

I am having the same problem.

---

