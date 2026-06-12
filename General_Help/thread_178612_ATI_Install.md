---
title: "ATI Install"
date: 2006-05-18
forum: General Help
---

### Post by anxie on 2006-05-18
Hi there. I just switched to linux a couple of days ago and its pretty rad. Must say I thought it would take a lot more tweaking then it did. Anywayz..

My problem is probably just small. I'm trying to install the ATI drivers and I run the installer:
```

==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install

```
My question is what do I do? lol

---

### Post by bluevoodoo1 on 2006-05-18
Could this guide perhaps help?
[http://ubuntuforums.org/showthread.php?t=75378&highlight=ati](http://ubuntuforums.org/showthread.php?t=75378&highlight=ati)

---

### Post by anxie on 2006-05-18
Well I followed that tutorial and everything seemed to go well but when I run fglrxinfo I get this:
```

OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by florizs on 2006-05-18
you should use the method from the wiki
binary ATI drivers.
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29%7C%28drivers%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29%7C%28drivers%29)

read from this part 
"Using the drivers from ati.com"

this is what worked for me,
good luck!

---

### Post by anxie on 2006-05-18
I managed to get it working good. Thx

---

