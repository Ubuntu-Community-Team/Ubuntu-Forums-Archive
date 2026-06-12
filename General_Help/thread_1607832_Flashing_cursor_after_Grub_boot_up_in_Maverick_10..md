---
title: "Flashing cursor after Grub boot up in Maverick 10.10"
date: 2010-10-28
forum: General Help
---

### Post by louis058 on 2010-10-28
I installed Ubuntu a while ago, but sometimes (about half the time), when I boot my computer, go into the Grub bootloader, then whether Grub selects Ubuntu for me (not sure if this is an error as well, but I've found that if I leave it without pressing any keys, then Grub just boots into Ubuntu for me (also, it's the top option)) or I select Ubuntu, it then flashes a cursor (a '_' character) on the screen (it's also in the same font as the font used by BIOS, so I assume at this moment, it's in BIOS).

Next, one of two things happen. Either I have to wait a few seconds, then it boots into Ubuntu, OR, it just hangs like that, not booting into Ubuntu, and not responding to any key presses or anything, forcing me to power off my machine using the hardware button.

I've searched in the forums and on the Internet, seemingly finding nothing that really helps, but I wanted to know whether anyone knows why this happens and how to fix it please.

My specs, generated from hardinfo, are:

```

-Computer-
Processor	        : 2x Intel(R) Core(TM)2 Duo CPU E6550 @ 2.33GHz
Memory		        : 2059MB (991MB used)
Operating System	: Ubuntu 10.10
-Display-
Resolution		: 1680x1050 pixels
OpenGL Renderer		: ATI Radeon HD 2400 XT
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
-Input Devices-
 Power Button
 Power Button
 USB Optical Mouse
 Dell Dell USB Keyboard
-Printers (CUPS)-
HP-Color-LaserJet-CP1514n
-SCSI Disks-
ATA SAMSUNG HD321KJ
TSSTcorp DVD+-RW TS-H653B
TEAC USB   HS-CF Card
TEAC USB   HS-xD/SM
TEAC USB   HS-MS Card
TEAC USB   HS-SD Card

```

---

### Post by P4man on 2010-10-28
Try this: in grub, rather than pressing enter on the default ubuntu kernel, press E (for edit). Edit the line that ends with "quiet splash" and remove those two options (so its not quiet and doesnt try to show a boot splash). Then hit control+x to boot.

If it gets stuck now, there is a good chance you will at least see where its stuck on.

This change only applies for a *single boot*, so you each time you reboot you will have to do it again, or make the change permanent by editing /etc/default/grub 

```
gksudo gedit /etc/default/grub 
```

remove quiet and splash there. Then run

```
sudo update-grub
```

BTW, rather than hitting the reset button, always try REISUB first:
[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

