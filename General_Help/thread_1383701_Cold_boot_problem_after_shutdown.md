---
title: "Cold boot problem after shutdown"
date: 2010-01-17
forum: General Help
---

### Post by walzing on 2010-01-17
Hi,
 
I currently try to move my HTPC to Linux. This is my hardware config:
[SIZE=1]**HTPC:** Antec Fusion Remote | MSI P7NGM-Digital | C2D E5200 | Scythe Shuriken Rev.B | GeIL Value DIMM 2GB PC2-6400U | WD Green 500GB | BeQuiet StraightPower 350Watt | LG GGC-H20L | Technotrend S2-1600 | Windows 7 | MP 1.1[/SIZE] SVN
 
So I started to install a mini ubuntu 9.10 and installed drivers, xbmc and vdr. 
**Repos:**
```

[SIZE=3][FONT=Calibri]add-apt-repository ppa:nvidia-vdpau/ppa[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]add-apt-repository ppa:team-xbmc[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]add-apt-repository ppa:the-vdr-team/vdr-ubuntu-karmic[/FONT][/SIZE]

```
**Driver:**
```

[FONT=Calibri][SIZE=3]cd /usr/src[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]hg clone http://linuxtv.org/hg/v4l-dvb[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]cd v4l-dvb[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make menuconfig[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]make install[/FONT][/SIZE]

```
 
It seems to work very nice, except one showstopper!!!
 
When I do a
```
shutdown -h now
```
the system will not be able to boot again. The Power-LED will go on, I hear fans and I hear the hdd. I can also see the DVD Drive blinking. But there is no BEEP and the screen stays black.
I have to unplug the power cable and wait at least 10 seconds (with pressed powerbutton), to get it back. 
 
First I would think it is a hardware problem. But my Windows is on /dev/sda1 and doesn't have this problem. Windows works fine with Power Off and S3 Standby...
 
**Just for information:**
I have installed ubuntu to partition 3 (sda5). I still use windows boot loader and did a dd on mbr:
```
dd if=/dev/sda of=mbr.img bs=512 count=1
```
I moved to mbr.img to C:, added linux to windows boot menu with bcdedit and rebuild mbr for windows.
 
This problem also occurs, when doing a pm-suspend.
 
For further information I have added my dmesg.
 
I hope someone has an idea - so thx in advance.
 
cu
Walzing

---

