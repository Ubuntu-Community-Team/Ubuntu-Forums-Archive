---
title: "configure: error: Cannot find X11 headers/libraries"
date: 2006-02-20
forum: General Help
---

### Post by shams2 on 2006-02-20
hi,
i want to install bmp-0.9.7 from the source with ./configure --prefix=/usr/  this is the error:
appending configuration tag "F77" to libtool
checking for beep-media-player... no
checking for X... no
configure: error: Cannot find X11 headers/libraries
pleas help me?

---

### Post by zappa86 on 2006-02-21
you need to get the X11 dev files. I believe the package is called libx11-dev and you could either synaptic it or:
```
sudo apt-get install libx11-dev
```

---

### Post by shams2 on 2006-02-21
thanks for reply that problem solved now onece again ./configure --prefix=/usr/ error:
checking for IceConnectionNumber in -lICE... yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.4.0 gtk+-2.0 >= 2.4.0 gthread-2.0 pango... configure: error: Cannot find glib2/gtk2/pango

---

### Post by matrixcosmos on 2007-12-28
> **zappa86 said:**
> you need to get the X11 dev files. I believe the package is called libx11-dev and you could either synaptic it or:
```
sudo apt-get install libx11-dev
```


I have same problem: Cannot find X11 headers/libraries. And I try to install libx11, but I get this: Coudn't find package libx11-dev. What do i gotta do?
/Sorry about my bad English.

---

### Post by Worp8d on 2008-04-18
I have the same problem and installed libx11-dev but the problem remains the same.  I'm running Ubuntu 8.04,

---

### Post by Stunts on 2008-04-18
@ Matrixcosmos:
I'm no expert in this sort of thing, but I'm guessing you have to enable the universe repositories. (System - Administration - Software sources). Make sure that they are enabled, and then try again. Maybe you also have to type
```
 sudo apt-get update 
```
after you enable the universe repros...
I hope this helps...
Tough, keep in mind that I'm no expert here.

---

### Post by f4csa on 2008-06-14
Hi !

I'm facing the same problem 
(configure: error: Cannot find X11 headers/libraries)
when trying to install bmp 0.9.7.1 for sources, and That package saved me : 
xorg-dev

Please note i'm running ubuntu 8.04

Hope this helps!

---

### Post by devehf on 2008-06-14
I'm also trying to install bmp-0.9.7.1 so I can run mp3splt-gtk. I installed bmp experimental but the mp3splt-gtk installer doesn't recognize that version of bmp. 

after Config I also get:
configure: error: Cannot find X11 headers/libraries

libx11 is already installed for sure:
"libx11-dev is already the newest version."

ubuntu 8.04

---

### Post by devehf on 2008-06-14
OK getting a little further after installing xorg-dev. 

Now the error is: checking for libglade-2.0 >= 2.3.1... configure: error: Cannot find libglade

---

### Post by devehf on 2008-06-14
Getting further after installing libglade-dev...

checking for ogg >= 1.0 vorbis >= 1.0 vorbisfile >= 1.0... configure: error: Cannot find libogg/libvorbis

---

### Post by devehf on 2008-06-14
installed libvorbis-dev and had success!

---

### Post by devehf on 2008-06-14
Oye! it turns out that installing BMP might be irrelevant!

First of all this old version doesn't seem to run at all. 

Second, this is what the mp3splt-gtk install file says:

```
-by default, beep-media-player support is disabled
However, if you need beep media player support, you can do :
	./configure --enable-bmp
```

---

### Post by nearownkira on 2008-07-08
after i typed in

./configure -prefix=usr
make
make install

all sucessful without any error

now I want to open beep media player, but i cant find where is it.how to find?

---

