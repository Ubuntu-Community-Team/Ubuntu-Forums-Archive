---
title: "Cant build my own kernel"
date: 2005-03-13
forum: General Help
---

### Post by MicroChris on 2005-03-13
Hey there,

Im trying to build my own kernel, and it wont let me.. Im trying to build 2.6.11.3. I cd'd to /usr/src. made the linux folder, unpacked the file, and did everything up right, but when I run "make menuconfig" or "make gconfig" this is what I get:

```
root@ubuntu:/usr/src/linux # make gconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** [scripts/kconfig/.tmp_gtkcheck] Error 1
make: *** [gconfig] Error 2
``` 


```
root@ubuntu:/usr/src/linux # make menuconfig
  SHIPPED scripts/kconfig/zconf.tab.h
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2
``` 

Thanks in advance for any help.

-Chris

---

### Post by MicroChris on 2005-03-13
Nevermind, figured it out...

Thanks!

---

### Post by az on 2005-03-13
Needed the -dev packages, huh?

(libgtk2.0-dev)

---

### Post by MicroChris on 2005-03-13
Now Im getting this:

```
root@ubuntu:/usr/src/linux # make modules_install
  INSTALL arch/i386/crypto/aes-i586.ko
cp: cannot stat `arch/i386/crypto/aes-i586.ko': No such file or directory
make[1]: *** [arch/i386/crypto/aes-i586.ko] Error 1
make: *** [_modinst_] Error 2
``` 

:-(

---

### Post by MicroChris on 2005-03-13
It seems that all the .o files are supposed to be .ko..

I dont get it :-(

---

### Post by az on 2005-03-13
sudo apt-get install build-essential kernel-package fakeroot

fakeroot make-kpkg --revision=1 --append-to-version=-4-386-whatever kernel_image modules_image kernel_headers



Wait.  You are trying to build some modules.  Why are you building your own kernel?  Is it just to make some modules?  Why not just use the linux-headers package.  That is what it is there for.  To make modules.

---

### Post by MicroChris on 2005-03-13
Im building the newest kernel (2.6.11.3) cause I dont think I can apt-get update/upgrade for it, can I?

Thanks,
Chris

---

