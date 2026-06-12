---
title: "can get XDebug working"
date: 2010-08-08
forum: General Help
---

### Post by prasanthsd on 2010-08-08
Hi guys,

Im running Ubunut 10.04 64 bit. I have installed apache2-mpm-prefork with apt. I needed php 5.2 so compiled 5.2.14 from source using the following configuration
```

'./configure'  '--with-apxs2=/usr/bin/apxs2' '--with-openssl'  '--with-zlib' '--with-bz2' '--with-curl' '--enable-calendar'  '--enable-exif' '--enable-ftp' '--with-gd' '--enable-gd-native-ttf'  '--with-mysql' '--with-mysqli' '--with-pdo-mysql' '--with-pear'  '--disable-maintainer-zts' '--enable-sockets' 
```then have done "pecl install xdebug" which generated the file /usr/local/lib/php/extensions/no-debug-non-zts-20060613/xdebug.so

added zend_extension="/usr/local/lib/php/extensions/no-debug-non-zts-20060613/xdebug.so"

Xdebug dosent showup in phpinfo(). Also tried to compile xdebug from source that didnt work either. It dosent display any errors on startup. If I use extension instead of zend_extension it doesnt throw any errors either.

Hoping that you guys will have some solutions. Thanks

---

### Post by prasanthsd on 2010-08-08
update: Using dl() from commandline i could actually load xdebug. it spawns a warning that it must be laoded as a zend extension. is this whole thing related to zendexenstionmanger.so? where can i donwload it? searched around in zend website but couldnt find anything.

---

### Post by lpanebr on 2010-10-14
Hi, 

Try adding the following line to your /etc/php5/apache2/php.ini file:

zend_extension=/usr/lib/php5/20090626/xdebug.so

It does not matter where but I put mine after the
;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;
section

If after having it show up in your phpinfo() you do not get a beautiful var_dump it's probably because you also need to make sure to set html_errors = On on your php.ini file.

regards,

---

