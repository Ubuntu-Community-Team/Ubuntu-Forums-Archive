---
title: "autoconf? PHP/Xdebug"
date: 2011-06-25
forum: General Help
---

### Post by Chris Psycho on 2011-06-25
Hey guys, I'm trying to install Xdebug on my XAMPP installation on ubuntu.

```

chris@chris-desktop:~$ sudo /opt/lampp/bin/pecl install Xdebug
downloading xdebug-2.1.1.tgz ...
Starting to download xdebug-2.1.1.tgz (303,198 bytes)
..............................................................done: 303,198 bytes
66 source files, building
running: phpize
grep: /opt/lampp/include/php/main/php.h: No such file or directory
grep: /opt/lampp/include/php/Zend/zend_modules.h: No such file or directory
grep: /opt/lampp/include/php/Zend/zend_extensions.h: No such file or directory
Configuring for:
PHP Api Version:
Zend Module Api No:
Zend Extension Api No:
[B]Cannot find autoconf. Please check your autoconf installation and the
$PHP_AUTOCONF environment variable. Then, rerun this script.[/B]

ERROR: `phpize' failed
chris@chris-desktop:~$ 

```I tried this: 
```

chris@chris-desktop:~$ whereis autoconf
autoconf:

```Can someone point me in the right direction?

---

### Post by Chris Psycho on 2011-06-26
bump

---

### Post by Chris Psycho on 2011-06-27
Should I have a go at (re)installing autoconf?

---

### Post by dragonfly41 on 2011-06-27
Can't answer your autoconf question ..

If it helps I followed the tips here to install xdebug ..

[http://djpate.com/2011/02/20/how-to-setup-xdebug-on-ubuntu-10-10/](http://djpate.com/2011/02/20/how-to-setup-xdebug-on-ubuntu-10-10/)

my xdebug.so is located in ..

/usr/lib/php5/20090626+lfs/xdebug.so

and in

/etc/php5/apache2/conf.d/xdebug.ini

I have one line ..

zend_extension=/usr/lib/php5/20090626+lfs/xdebug.so



[EDIT]

see also here ..

[http://www.spiration.co.uk/post/1385/Cannot-find-autoconf.-Please-check-your-autoconf-installation](http://www.spiration.co.uk/post/1385/Cannot-find-autoconf.-Please-check-your-autoconf-installation)

---

