---
title: "mplayer on hoary"
date: 2005-03-14
forum: General Help
---

### Post by elwis on 2005-03-14
I'm trying to compile Mplayer on my hoary (since the apt-get one segfaults on me)

Anyway, when running "make" I get

> 
/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status


Any idea about what's wrong??

---

