---
title: "Unable to compile or build ImageMagick, et al"
date: 2010-09-20
forum: General Help
---

### Post by eholz1 on 2010-09-20
Hello All,

I have tried in vain to install either gmagick or imagick for php
on my ubuntu system.  I am running 9.10 server. Pecl, not work.
Tried to build from source - gcc compiler errors with 
something about ld error - report this bug, etc.
my gcc version is 4.4.1.  I have used phpize, then ./configure, etc. No luck.  I do have apache2 and PHP 5.2 with pear running, etc.

Does anyone know if Imagemagick can be installed on Ubuntu server?
I have a website with a lot of php pages that use the MagicWand constructor, etc.

Thanks

eric

---

### Post by andrewthomas on 2010-09-20
[http://packages.ubuntu.com/karmic/imagemagick](http://packages.ubuntu.com/karmic/imagemagick)

---

### Post by eholz1 on 2010-09-21
Thanks, I will check this out!

---

### Post by eholz1 on 2010-10-06
Hello All,

I have installed Ubuntu server 10.04.  I have attempted
to use cc and gcc (did install build-essentials).

I get the same error in regard to the ld message.

I guess I will not attempt to compile programs or build things.

thanks,

eholz1:(

---

### Post by SeijiSensei on 2010-10-06
After you've run 'make install' try running 'sudo ldconfig' and see if that helps.

Usually most compatible source code installs under /usr/local and places the libraries in /usr/local/lib.  On my Maverick machine, there is a file called libc.conf in /etc/ld.so.conf/ that contains the line "/usr/local/lib".  If you don't have that, create /etc/ld.so.conf/libc.conf with just the line /usr/local/lib, then run 'sudo ldconfig'.

---

### Post by andrewthomas on 2010-10-06
> **SeijiSensei said:**
> After you've run 'make install' try running 'sudo ldconfig' and see if that helps.

Usually most compatible source code installs under /usr/local and places the libraries in /usr/local/lib.  On my Maverick machine, there is a file called libc.conf in /etc/ld.so.conf/ that contains the line "/usr/local/lib".  If you don't have that, create /etc/ld.so.conf/libc.conf with just the line /usr/local/lib, then run 'sudo ldconfig'.
Isn't it  /etc/**ld.so.conf.d**/libc.conf ?

---

### Post by SeijiSensei on 2010-10-06
Sorry, you're right, Andrew.  /etc/ld.so.conf.d/ is the directory.

---

