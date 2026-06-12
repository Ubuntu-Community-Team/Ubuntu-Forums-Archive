---
title: "Over scan on 1920x1080"
date: 2010-10-17
forum: General Help
---

### Post by iammagicboy on 2010-10-17
hi,lately I install the ubuntu 10.10.Everything seem right expect the resolution.I get an over scan problem on 1920x1080.I use ati 4650,I'm not sure if the driver is correct installed.I google it and I found that the problem was in my xorg.conf.I tried to fix it but I not know what my resolution is.How can I found the right resolution of my monitor(my visible resolution)?

---

### Post by iammagicboy on 2010-10-17
nobody?

---

### Post by efflandt on 2010-10-17
Does your monitor or HDTV have any setting in its menus to adjust or auto sync to the signal it is receiving?  Usually sync'ing would be easier with a digital connection (DVI or HDMI) than VGA.

I am using a 32" 1080p HDTV and even with DVI to HDMI cable (which should identify everything properly to video source) if I set the TV to normal 16:9 it is overscanned using nvidia drivers.  But fortunately my LG HDTV has a setting called "Just Scan" which attempts to size received signal full screen, and that works fine 1920x1080.

Unfortunately I do not really know where to put modelines in xorg.conf.  I originally got a modeline from /var/log/Xorg.0.log of my old PC using default ATI video for DVI to HDMI connection to figure out what to use in xrandr command when I connect VGA of my laptop to this HDTV.  That was somewhat different than I got from output of **cvt** or **gtf**

"1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync

---

### Post by iammagicboy on 2010-10-17
It worked!Thank you very much!!!!!

---

