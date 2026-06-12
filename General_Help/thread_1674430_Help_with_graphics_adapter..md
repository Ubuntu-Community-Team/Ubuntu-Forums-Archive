---
title: "Help with graphics adapter."
date: 2011-01-23
forum: General Help
---

### Post by skaldicpoet9 on 2011-01-23
Hey there everyone. I recently installed Ubuntu 10.10 on my laptop. It is an older laptop with a Radeon Xpress 200m video card, which apparently is unsupported by the newest version of the proprietary ATI drivers. Right now I am using the default graphics adapter that was installed, however, all of my games run abysmally. There isn't one game I have played (World of Goo, Gish, Eschalon Book I) that has played decently. They all suffer from screen flicker and tremendous slowdowns. Is there any option for me since the 200m is no longer supported by ATI?

---

### Post by Bucky Ball on 2011-01-23
[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

This is old but seems to work.

Also:

[http://au.altavista.com/web/results?fr=altavista&itag=ody&q=Radeon+Xpress+200m+Maverick+10.10&kgs=0&kls=0](http://au.altavista.com/web/results?fr=altavista&itag=ody&q=Radeon+Xpress+200m+Maverick+10.10&kgs=0&kls=0)

---

### Post by skaldicpoet9 on 2011-01-23
Thank you so much, I will try these out and post the results asap.

---

### Post by clhsharky on 2011-01-24
skaldicpoet9

xorg-edgers PPA would be your best bet, it has a fresher OSS drivers.
[https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)
Read whole page/*IMPORTANT NOTICE*

Also installing kernel (v2.6.38-rc2-natty/) from here
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc2-natty](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.38-rc2-natty)
will speed up your newer driver stack.

I have tested this r300g driver stack(this driver supports your Radeon Xpress 200m chip) and has almost double FPS on some games.

This stack is considered experimental so proceed with causation.

I have used xorg-edgers PPA for last two releases with out a failure your mileage may very.


Sharky

---

### Post by skaldicpoet9 on 2011-01-24
Okay, I am confused on what I am suppoed to do here. I followed the directions on the xorg-edgers website for adding the xorg-edgers ppa to the respository list, however, I don't know how to install the drivers. I searched in the repository list for ppa but the only thing that came up was the ppa-purge package. I also searched for the xorg driver, which oddly enough was listed but had exlaimation marks next to the package listing. I have read the xorg-edgers page several times and I am confused as to how to install the ppa. Are the xorg and xorg-serve-core packages the ones that I want to install?

---

### Post by skaldicpoet9 on 2011-01-25
Okay, I got it figured out. Apparently the existing packages are upgraded as indicated by the explanation points by the packages. However, when I upgraded to the xorg-edgers PPA the display became very erratic and wouldn't allow me to switch windows, as well as visual artifacts on the screen. Is there something that I did wrong? Was I supposed to uninstall the default graphics drivers frist or something?

---

