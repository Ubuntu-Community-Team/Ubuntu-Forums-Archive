---
title: "X11 Non-start issue"
date: 2006-02-20
forum: General Help
---

### Post by schenkin on 2006-02-20
X11 will not start properly on my machine, just so you know it is a 64bit AMD system (the proper release was installed) with an ATI Radeon 700x PCIx card (2x dvi connectors) with dual monitors running at 1680x1050 when it works. When I attempt to start X11 (startx), i get the following error: Skipping "/usr/bunchofjunkididn'twanttocoppyout" no symbols found (EE) No devices detected Fatal Server Error: No screens found I'd post the log but I can't mount the partition in windows (at least as far as I know) and setting up email without a GUI is beyond (I want to install Kubuntu to learn more about linux)

---

### Post by baldy1324 on 2006-02-20
heres some common errors when ubuntu configures x11-
-make sure that the mouse is /dev/input/mice-that always is bad
-make sure your moniter specs are done correctly

however since it talks about devices (aka graphics cards) it might be a bad driver
one time when i installed the ati driver didn't work-and i had to use the VESA DRIVER-AND IT WORKED(INSTEAD OF ATI DRIVER) note that it isn't 3d accelerated

---

### Post by schenkin on 2006-02-20
It looks ok, although admittedly I may not know the difference. I've tried to install several time but it hasn't worked. Is there a way to install a new driver?

--Sam

---

### Post by schenkin on 2006-02-20
Well, i fixed that issue using instructions here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

As things stand now however, the ATI Utility doesn't work (when I try to launch it is just "bounces" next to my cusor). Also, it is showing the same thing on both of my monitors, but I can probably figure that one out myself.

---

### Post by TD-Linux on 2006-02-21
I am having the same problem. Pentium 4 550, with an ATI X700PRO 256MB PCI-E graphics card (one dvi, one vga). I'm running in a simple single monitor setup. I followed the intructions [here]("http://ubuntuforums.org/showthread.php?t=80811") to install on my external USB drive. The installer worked perfectly up to the point that the text-based installer ended and it tried to start X. I got dropped to a terminal instead, where I could log on and do everything except start X, with many of the same errors as others have had.
I have successfully started X from a LiveCD (Knoppix).

How would I download the ATI driver from a terminal?

---

### Post by schenkin on 2006-02-21
run 

wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.22.5-i386.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.22.5-i386.run) --no-check-certificate,

Then follow the instructions to install that i linked at the top of the thread. I just downloaded them and burned to to CD in windows though if that is easier.

---

