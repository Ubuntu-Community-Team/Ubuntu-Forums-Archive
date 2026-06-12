---
title: "Ubuntu Maverick randomly crashes frequently"
date: 2011-02-11
forum: General Help
---

### Post by zdubya on 2011-02-11
Hello all,
Forgive me but I am new to linux.  I recently switched from windows 7 after my harddrive crashed and my laptop manufacturer replaced it.  They did not include a new copy of windows, which is why I started using Ubuntu.

My system is a new laptop (2010):
MSI s6000 i5-450m with Turbo Boost
intel hd graphics
4GB DDR3 SDRAM

Using:
Ubuntu 10.10 (maverick)
Kernel Linux 2.6.35-25 generic
GNOME 2.32.0

Problem:
My entire system randomly freezes, meaning the screen gets stuck like a screenshot, and the keyboard/mouse are completely unresponsive.  alt-f1 does nothing.  The only thing that works is Alt-sysrq-R-E-I-S-U-B.  I have been trying to figure out the common denominator to these crashes, but I can't pinpoint it.  It USUALLY happens when the system idles after about 5 minutes of no action.  I have the system monitor on my top panel and I notice no spikes.  My system runs very quickly when it's working properly.

Please advise me!  How do I diagnose this problem, or where should I begin?:confused:

---

### Post by zdubya on 2011-02-11
Whoops! Sorry about the triple post.

My system just crashed again.  It happens about once an hour, sometimes more.  I installed xsensors to monitor the temperature, and it says it's between 50-60 degrees celcius.  The programs I normally run are Transmission, Chrome, and Amarok.

---

### Post by zdubya on 2011-02-16
It seems to happen only when using Transmission

---

### Post by 4Orbs on 2011-02-16
> It USUALLY happens when the system idles after about 5 minutes of no action
My first guess would be that the screensaver is attempting to kick-in and load one of the more graphics-intensive 3D images... but the system freezes because you have not yet activated the driver for your graphics chip (thus you don't have 3D capability). If this is the case, you can either activate the driver (System menu>>Administration>>Additional Drivers) or disable the screensaver (set it to "Blank Screen Only" or disable).

---

### Post by zdubya on 2011-02-17
Okay, so it also happens when I'm using Vuse.  I think the problem is related to spikes in the network?  Such as when downloading large bit torrent files.  The system can idle and sleep just fine when I'm not downloading anything.  It's all about the torrents it appears.  I searched on the subject and saw some really old posts similar to this, but nothing recent.  Anyone else experience problems crashing with bit torrents?

---

