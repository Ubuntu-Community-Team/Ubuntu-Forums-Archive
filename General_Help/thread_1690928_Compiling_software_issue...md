---
title: "Compiling software issue.."
date: 2011-02-19
forum: General Help
---

### Post by littlebobby on 2011-02-19
Hello,

I am trying to build a piece of software but I am continually presented with the following message:

*** full path to libIDL-config.
checking for libIDL-2.0 >= 0.8.0... yes
checking LIBIDL_CFLAGS... -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking LIBIDL_LIBS... -lIDL-2 -lglib-2.0  
checking for glib-2.0 >= 1.3.7 gobject-2.0... yes
checking GLIB_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -pthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
/home/bobby/Thumbnails/offscreen/configure: 21229: no: not found
checking for stdint.h... yes
checking for inttypes.h... yes
checking for sys/int_types.h... no
checking for iwlib.h... yes
checking for fontconfig/fcfreetype.h... no
configure: error: Can't find header fontconfig/fcfreetype.h.
*** Fix above errors and then restart with               "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/bobby/Thumbnails/offscreen'
make: *** [/home/bobby/Thumbnails/offscreen/../obj-i686-pc-linux-gnu/Makefile] Error 2

However, fontconfig (libfontconfig1-dev) is already installed. The software I am trying to build is here:

[http://ted.mielczarek.org/hg/moz-headless-screenshot/file/tip/Makefile](http://ted.mielczarek.org/hg/moz-headless-screenshot/file/tip/Makefile)

I get this error from 'make -f client.mk'

Hope someone can help! Thanks :popcorn:

---

### Post by gavinjb on 2011-02-19
Hi,

My compiling knowledge is limited, but it looks like it is looking for the header file from fronconfig, my thought is either you need to install the source for fontconfig or the source you are trying to compile is expecting it in a different location to where it is.


Gavin,

---

### Post by lykeion on 2011-02-19
A tip is to use the *apt-file* command to search for packages containing the missing header file. First install apt-file (don't think it's installed by default):
```
sudo apt-get install apt-file
```
Then search for packages containing the missing header file *fcfreetype.h*:```
apt-file search fcfreetype.h
```
You'll get two results, and the best bet is to install the first one, i.e *libfontconfig1-dev*: ```
sudo apt-get install libfontconfig1-dev
```

---

### Post by littlebobby on 2011-02-19
> **lykeion said:**
> A tip is to use the *apt-file* command to search for packages containing the missing header file. First install apt-file (don't think it's installed by default):
```
sudo apt-get install apt-file
```Then search for packages containing the missing header file *fcfreetype.h*:```
apt-file search fcfreetype.h
```You'll get two results, and the best bet is to install the first one, i.e *libfontconfig1-dev*: ```
sudo apt-get install libfontconfig1-dev
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfontconfig1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

seems its already installed - should have probably mentioned that a little earlier :) any other suggestions?

---

### Post by littlebobby on 2011-02-21
Bump. Anyone have any ideas?

---

### Post by lykeion on 2011-02-22
Sorry can't help you any further. I tried to compile it myself, but got stuck at the hg clone command. My advice is to contact the author.

---

