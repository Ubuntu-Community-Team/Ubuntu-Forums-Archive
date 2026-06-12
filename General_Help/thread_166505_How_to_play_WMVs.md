---
title: "How to play WMVs?"
date: 2006-04-26
forum: General Help
---

### Post by chris062689 on 2006-04-26
Is there just some package I can download and install that ONLY adds support for WMV files?  I don't want all of this mp3 crap "bundle packs".

Isn't there some .deb package that automaticly installs a Movie Player (With WMV codecs?)

What's the best Movie player to use the codecs with?

---

### Post by Perfect Storm on 2006-04-26
You could try with VLC.

---

### Post by jazzmuzik on 2006-04-26
mplayer is the best IMO. It can play anything. The codecs bundle pack is actually a group of small files that tell audio and video players how to interpret the data. mp3 is just one of those codecs. wmv is another. When you install codecs they often come in a "pack". That's more convenient that installing a hundred individual packs.

Look at the restricted formats information:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by jazzmuzik on 2006-04-26
Yeah, VLC is a great suggestion.

---

### Post by Rog131 on 2006-04-26
Download w32codecs (12,6M):
[http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/i386/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb)

Install:
sudo dpkg -i w32codecs*.deb

More:
libdvdcss2 and w32codecs for Ubuntu
[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

Best ??

I have kaffeine, mplayer, vlc ... :-k

---

### Post by chris062689 on 2006-04-26
[deleted Due To Stupidity]

---

### Post by regeya on 2006-04-26
[QUOTE=chris062689]chris@ubuntu:~$ sudo dpkg -i w32codecs.deb
dpkg: error processing w32codecs.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs.deb
chris@ubuntu:~$[/QUOTE]

right, because there's no file by that name.  you forgot the wildcard.

---

