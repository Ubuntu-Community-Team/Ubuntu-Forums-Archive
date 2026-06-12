---
title: "XAMPP +XDebug"
date: 2011-04-14
forum: General Help
---

### Post by r.peel on 2011-04-14
Hello,

Can anyone help me set up XDebug to use with XAMPP?

I've tried a few different methods that I found through google, but either It wouldn't work, and I have no idea why, or I seemed to be missing other applications in order to build the module.

If any one has a, complete, working guide I would be grateful

---

### Post by dragonfly41 on 2011-04-19
If you haven't got XDebug to work yet .. I've just gone through the process with lamp

I found this

[http://theindexer.wordpress.com/2009/02/03/installing-xdebug-on-ubuntu-lamp-stack-using-apt/](http://theindexer.wordpress.com/2009/02/03/installing-xdebug-on-ubuntu-lamp-stack-using-apt/)

To find the location of xdebug.so and its path

sudo find / -name 'xdebug.so' 2> /dev/null

which showed this for me ..
/usr/lib/php5/20090626+lfs/xdebug.so

I pasted that path into php.ini  at   /etc/php5/apache2/php.ini file:

zend_extension=/usr/lib/php5/20090626+lfs/xdebug.so

and added ..

xdebug.default_enable=On
xdebug.extended_info=1
xdebug.show_local_vars=1

Restarted apache

sudo /etc/init.d/apache2 restart

checked [http://localhost/~]("http://localhost/%7E")[whoami]/phpinfo.php

and xdebug was seen in phpinfo report.



[edit]

And ..

sudo gedit /etc/php5/apache2/php.ini

display_errors = On
html_errors = On

sudo /etc/init.d/apache2 restart

---

