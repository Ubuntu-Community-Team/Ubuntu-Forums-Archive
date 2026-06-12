---
title: "No Flash on 10.04 x64?"
date: 2010-04-30
forum: General Help
---

### Post by whiskeylover on 2010-04-30
Just installed 10.04 64 bit, and can't install flash player from the software center. Does anyone else have this problem? Does anyone have a solution?

---

### Post by philinux on 2010-04-30
I would do this for 64 bit as synaptic will only install the 32 bit flash and it's a bit buggy.

Get this file from adobe.
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Right click and extract here.
You'll find the file libflashplayer.so inside the archive.

Create this directory ~/.mozilla/**plugins**

Move or copy the file into this new directory. Restart Firefox.

---

### Post by lovinglinux on 2010-04-30
Install the 64bit beta version. 

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by whiskeylover on 2010-04-30
Weird... when I tried installing the flash plugin in the Live CD environment, it failed. But it worked after the full install. Everything worked after I installed it from the USC.

Thanks for the reply guys.

---

### Post by Kilz on 2010-04-30
> **whiskeylover said:**
> Weird... when I tried installing the flash plugin in the Live CD environment, it failed. But it worked after the full install. Everything worked after I installed it from the USC.

Thanks for the reply guys.

Installing thing while running under the live cd is, if not impossible, extremely hard.

---

### Post by whiskeylover on 2010-04-30
> **Kilz said:**
> Installing thing while running under the live cd is, if not impossible, extremely hard.

Got it. Thanks : )

---

