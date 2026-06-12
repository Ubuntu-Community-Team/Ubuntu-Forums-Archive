---
title: "Problem with xmms install"
date: 2005-02-06
forum: General Help
---

### Post by Kimimaro on 2005-02-06
After unpacking the xmms-1.2.10.tar.gz from [www.xmms.org](www.xmms.org) i tried to proceed with the instructions (first command [in the unpacked directory with files] given from the terminal is suposed to be ./configure). After typing ./configure in the proper directory (xmms-1.2.10) all I got was :
" 
Kimimaro@ubu:~/Xmmsprog/xmms-1.2.10 $ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
"

commands after 'make' (like make install) just don't work ... help ?  :-(

---

### Post by christooss on 2005-02-06
Why dont you install xmms with apt-get?

[Check it in Ubuntu starter guide how to install xmms](http://ubuntuguide.org/#xmms)

---

### Post by Kimimaro on 2005-02-06
Ok, I've installed it, thank you.  But when I try to run it (either from apps/multimedia/xmms or from the terminal ) it does not execute...
I mean when I'm opening it from the apps/multimedia there is some 'action' :mrgreen: (HDD sound, and an aplication pops up,for a blink of an eye, then it dies), however thats all, no window, no anything...
And when I try to run it from the terminal I get the following error : 
"

kimimaro@ubu-216-228:~ $ xmms
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

"
... I'm confused

---

### Post by christooss on 2005-02-06
DId you installed all codecs with

 $ sudo apt-get install gstreamer0.8-plugins
 $ sudo apt-get install w32codecs

---

### Post by Kimimaro on 2005-02-06
"
kimimaro@ubu-216-228:~ $ sudo apt-get install gstreamer0.8-plugins
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
"

"
kimimaro@ubu-216-228:~ $ sudo apt-get install w32codecs
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package w32codecs
"

 :shock:

---

### Post by Kimimaro on 2005-02-06
Any ideas anyone ? :sad:

---

### Post by christooss on 2005-02-06
You have to add all of the repositories. Check this page

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

