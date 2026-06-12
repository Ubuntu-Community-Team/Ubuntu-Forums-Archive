---
title: "Well, this is weird..."
date: 2011-02-07
forum: General Help
---

### Post by u-noob-tu on 2011-02-07
I've been trying to setup a dual monitor on my computer for awhile, and tonight I finally got xorg.conf all configured (although it would seem that I messed up something) and put it in /etc/X11/ and rebooted to see a message right before I get to the login screen that says "your system does not support DMA. please use PIO instead". And then it mentions b43, which is the firmware number of my wireless driver. So I went into low graphics mode and discovered that the driver had been deactivated and maybe even uninstalled (it just said "activate"). So I reinstalled it and still get the same error. I'm confused. Xorg.conf has nothing to do with the wireless card, right? I would just replace the xorg.conf with a backup but the backup was somehow copied over by the new xorg.conf and it's gone. I'll post the current xorg.conf as soon as I can (I'm doing this in a restaurant on my iPod). I'm pretty confused. Any ideas?

---

