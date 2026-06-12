---
title: "wine installation help"
date: 2006-06-19
forum: General Help
---

### Post by killzoneman0 on 2006-06-19
wine supports i386 and i have an amd system, which isnt i386.  is there any way that i can get wine installed on my system?

---

### Post by RAOF on 2006-06-20
AMD processors are, among other things, i386 processors - they support the IA32 instruction set, which is what the i386 refers to.  As such, you should be able to just install it.

Unless you installed the AMD64 version of Ubuntu.  Then, the package manager (apt) doesn't know that your processor is also an i386, so you have to tell it to ignore the difference.  You can download the binary deb from the wine site, and then run (from a terminal)
```
sudo dpkg --install --force-architecture *the_wine_file.deb*
```
obviously replacing *the_wine_file.deb* with the name of the wine .deb file you downloaded.

---

### Post by bforbes on 2006-06-20
I run AMD64 Breezy, but I wanted to run Wine in a 32-bit environment just in case. I made a 32-bit chroot and installed Wine in there. This guide is good for starters:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=32+bit+chroot)

---

