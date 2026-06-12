---
title: "Error when trying to build NeL  (OpenAl)"
date: 2009-09-25
forum: General Help
---

### Post by Sarteck on 2009-09-25
I was going to try to muck around with creating a small MMO, just to see what it entails and if it's something I could get into.  It seems that NeL is the best choice for this (please recommend other engines if you know of them).  I was going to install both the client and server on my local machine to test things out, or so I thought.

Unfortunately, I can't seem to get it to configure with sound.  It requires either OpenAl or FMod3, and I've been trying to install both.

For OpenAl, I went to the OpenAl site, downloaded it, and followed the instructions for CMake.  It SEEMS that it installed correctly, but when trying to **./configure --with-gtk --enable-sound** NeL, it gives me this error:```
checking for FMOD headers... no
checking for FMOD libraries... no
checking for OpenAL headers... yes
checking for OpenAL libraries... no
configure: error: Either FMod or OpenAL must be installed to use sound.
```Now, when I don't use the **--enable-sound**, I don't get any errors, but I'd really like to find out why Sound ain't working.


Relevant info:
```

sarteck@Auron:~/code/nel$ openal-config --libdir
/usr/lib
sarteck@Auron:~/code/nel$ openal-config --version
1.3.253
sarteck@Auron:~/code/nel$ openal-config --libs
 -lopenal
sarteck@Auron:~/code/nel$ ls -l /usr/lib/libopenal*
-rw-r--r-- 1 root root 311774 2008-12-01 04:54 /usr/lib/libopenal.a
lrwxrwxrwx 1 root root     14 2009-09-25 00:02 /usr/lib/libopenal.so -> libopenal.so.1
lrwxrwxrwx 1 root root     20 2009-09-24 23:58 /usr/lib/libopenal.so.1 -> libopenal.so.1.4.272
-rw-r--r-- 1 root root 162872 2008-12-01 04:54 /usr/lib/libopenal.so.1.4.272

```

Could someone give me a nudge in the right direction?

---

### Post by Sarteck on 2009-09-25
P.S., I've also tried FMod with similar luck, but gave up on FMod when I was reading that it hogs system resources.  (I don't know if this is true or not, tbh, though.)

---

