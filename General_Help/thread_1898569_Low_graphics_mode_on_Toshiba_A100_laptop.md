---
title: "Low graphics mode on Toshiba A100 laptop"
date: 2011-12-21
forum: General Help
---

### Post by dishbert on 2011-12-21
Since I restored my dual boot XP and 10.04 system after a hard drive replacement I get "Ubuntu is running in low-graphics mode" every time I boot up.

If I select "restart X" from the menu that appears after the warnings everything works fine.

Here are some particulars:

$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

Searching for hardware drivers only finds a software modem driver.

The tail end of the xorg1.log looks like this:

(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:05:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

The xorg.conf file is pretty basic:

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

I'm sure the answer is obvious in the data above, but not to me! What do I need to fix?

(This is for my laptop, not the hardware details in my signature block.)
__________________
dishbert

---

