---
title: "having issues with ati driver"
date: 2009-11-06
forum: General Help
---

### Post by nerdy_kid on 2009-11-06
hey all, i downloaded the ati radeon Xpress (integrated) driver from ati, everthing installed fine, but now gdm displays:

```

The following error was encountered. You may need to update your configuration to solve this.


(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module 'glx' (loader failed, 7)
(EE)  Failed to load module 'fglrx' (module requirement mismatch, 0)
(EE) No drivers avalible



```


ive tryed envyng and got a frozen screen of colored static.
ive tryed ubuntu's version of the drivers and the same thing happens.

?????

---

### Post by anilsarwal on 2009-11-06
**Ubuntu 9/10 does not pick up video drivers for ASUS M2N68-AM - motherboard - micro ATX - GeForce 7025 and Processor      AMD Athlon(tm) 64 X2 Dual Core Processor 5000+, 2600 Mhz, 2 Core(s), 2 Logical Processor(s). Can anyone help in booting to the desktop gui.**

---

### Post by nerdy_kid on 2009-11-06
the system is running jaunty

---

### Post by jbrown96 on 2009-11-06
How old is the graphics card? When you downloaded the driver from ATI, did it say anything about legacy?

ATI has horrible drivers. In May, they decided to cut off support for older cards. This means that the current catalyst (fglrx) driver does not work with your card. Unfortunately, you can't use an older version of the card because it does not support the X-server that 9.10 uses. 

On the up side, the open source drivers that are included by default are getting pretty good, and you shouldn't have much problem with them. When you boot the system, you probably get a menu that has several kernels available. Choose the second one on the list, which should be for recovery. Once it boots, you should get an option to fix the x-server, or if not, choose the root shell and run the following ```
sudo dpkg-reconfigure --xorg-xserver
``` that will walk you through setting everything up. If you use a US keyboard, then you can accept all the defaults during this process.

---

### Post by nerdy_kid on 2009-11-06
ok, thanks for the info.  I am assuming the open source drivers you mention are mesa right?

---

### Post by jbrown96 on 2009-11-06
The graphics stack is really complicated, and I don't understand it fully. Mesa is one part of that, so I would imagine that the driver would be named that.

---

### Post by nerdy_kid on 2009-11-06
ok, thanks.  Got it working :D

---

