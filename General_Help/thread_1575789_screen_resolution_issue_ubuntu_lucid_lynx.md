---
title: "screen resolution issue ubuntu lucid lynx"
date: 2010-09-16
forum: General Help
---

### Post by mistikkia on 2010-09-16
Hello,

I happen to have a Fujitsu Siemes Esprimo Mobile laptop which seems to have some issues with screen resolutions in Ubuntu (currently running lucid lynx 64 bit edition) ... it did not with Fedora though.
After spending days and days trying to see what is wrong and how I can fix it I managed to discover the sis671 driver which I downloaded and copied the files sis671_drv.la  and sis671_drv.so to /usr/lib/xorg/modules/drivers and also started playing with the /etc/X11/xorg.conf which currently looks like this :

Section "Device"
       Identifier      "Device0"
       Driver          "sis671"
       VendorName      "Silicon Integrated Systems [SiS]"
EndSection

Section "Screen"
       Identifier "Screen0"
       Device     "Device0"
       Monitor    "Monitor0"
       DefaultDepth     16
       SubSection "Display"
               Viewport   0 0
               Depth     16
               Modes   "1024x800"
       EndSubSection
EndSection

I can now choose 1280x800 at 60 Hz (or so says my Prefrences -> Monitors dialog box) but it still quite big so I was wondering if any of you guys that have the same laptop can post your /etc/X11/xorg.conf file. I managed to fix my problem just by playing with my file and putting random stuff in it so I think I might have a chance of improving it should I get the right stuff in there... 
I am also open to any new suggestions as well

M.

---

### Post by mistikkia on 2010-09-16
I see this is a fairly common problem, but can't find an answer that would work.

---

### Post by mistikkia on 2010-09-23
funny thought - should i tinker with it and see if i can get it working with 2 screens :P

---

### Post by mistikkia on 2010-09-25
bump

---

### Post by mistikkia on 2010-10-12
bump

---

