---
title: "Not getting any video using Nvidia Geforce GT 240"
date: 2011-01-18
forum: General Help
---

### Post by Xaqre on 2011-01-18
Built a custom pc using a Gigabyte mobo and amd processor. Mobo has onboard video. Ubuntu Maverick installs fine using on board video but when I put in the Nvidia Geforce GT 240 I get either no video or scrambled video. I've tried disabling the on board video and still no luck. I've also tried to install nvidia drivers first, and will get it to work but video is not crisp and will not show all of the screen. I'm new to Ubuntu.....a few years as a hobby, so I don't know much on how to troubleshoot so please respond with increased patience. Thank you for any help provided in advance.

---

### Post by Terry32 on 2011-01-19
Same issue here, running evga GT 240 on an AMD 64 5000+ Dual Core with 2GB ram on an Asus motherboard with the 570 SLI chipset. Can't install with the Ubuntu 10.10 or Kubuntu 10.10 disks, only tried 32 bit versions. I tried to install with and older card and then putin the GT240 but it results in black screen, or boot install disk with GT240 in and I get wierd garbled video that is just a bunch of colored pixels.
 
I also tried 10.04 which works until I update, seems like things have been slowly sliding downhill for Ubuntu since the 8.04/8.10 days.

---

### Post by yetiman64 on 2011-01-19
On setting up my GT240, to get it working I had to set it up in BIOS by changing the settings "Init Display First" to "PCIEx" (your settings may be named differently - this gets BIOS to look to the card 1st and not use the internal graphics "IGX".)

> I've tried disabling the on board video and still no luck.Also I still had problems, until I disabled the setting for "Memory Hole" in BIOS for graphics. Had no graphics work until it was disabled with the card in use. 

Use caution changing any BIOS settings as you can render a system unbootable or possibly do hardware damage. 

Once setup in BIOS correctly the card was usable as normal and I installed drivers initially from System > Administration > Hardware Drivers (installed the "Current" drivers). Have since updated drivers to x-swat ppa, though this is not usually necessary for most users.

There should be no need to install drivers for this card just to load the system. If BIOS settings are correct, you should only need to load drivers if you want 3d acceleration etc.

---

### Post by Xaqre on 2011-01-19
I've played with some of the settings in the bios but the last suggestion; about the "memory hole" I have yet to try. I'll give it a shot and see what I come up with.....thanks

---

### Post by Xaqre on 2011-01-24
Tried finding the settings in the bios that you spoke of (memory hole) and didn't see anything. I tried a few other settings but to no avail. I finally gave up and went back to 10.04 instead of 10.10 and everything installed fine. However, now I don't have sound and that's a whole new problem. I'm not sure what else to try. On one hand I have 10.10 with no video and on the other I have 10.04 with no sound. I'd like to stay with the 10.10 but unless someone else has some other ideas I'm kinda stuck. Thanks again for any assistance in advance.

---

