---
title: "Newly installed graphics card results in X failing"
date: 2010-08-12
forum: General Help
---

### Post by ejn114 on 2010-08-12
Hi,

Today I replaced my desktop's old Radeon HD 3850 with a new Radeon HD 5670.  My system dual boots Lucid and Windows 7.  Setup in Windows 7 was fine and the card now works.

In Ubuntu, though, I see the Ubuntu loading screen, and then X fails to start and I'm given a blank screen.  I booted into recovery mode and started with failsafe graphics; this allowed me to select an option to reconfigure with new hardware.  Unfortunately, this didn't help.  I perused some older threads on this sort of topic here and tried: 

sudo dpkg-reconfigure xserver-xorg 

from the root terminal accessible in recovery mode.  Nothing happened.

What should I try next?

Thanks,

EJN

---

### Post by dino99 on 2010-08-12
you may need to remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

then check driver activation: system admin hardware driver

then reboot

*** some ati system need to add nomodeset on the boot line (/etc/default/grub) then run update-grub again

---

### Post by ejn114 on 2010-08-12
I followed your instructions as best I could.  X is starting now, but I don't have any video.  Audio works and I get the Ubuntu start sound when X starts.  The screen remains black the whole time.

How do I edit the stuff in grub?  Does anyone else have any suggestions?

---

### Post by ejn114 on 2010-08-12
Maybe this will help:

Running lspci | grep VGA yields "01:00.0 VGA compatible controller: ATI Technologies Inc Device 68d8".

Running sudo lshw -C video gives:

*-display UNCLAIMED
description: VGA compatible controller
product: ATI Technologies Inc
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: latency=0
resources: memory:e0000000-efffffff(prefetchable) memory:f5000000-f501ffff ioport:b000(size=256) memory:f4000000-f401ffff(prefetchable)

---

### Post by ejn114 on 2010-08-12
I used a DVI to VGA adapter and ran a VGA cable into my (DVI-capable) monitor.  I can now see things again...but why can I not use DVI?

---

### Post by ejn114 on 2010-08-12
I was able to solve this myself, ultimately, by updating to the latest fglrx drivers, switching to VGA, running aticonfig --initial, and then rebooting with DVI connected.

---

### Post by mantaor on 2010-08-15
Enj thanks for your experience, i wish to buy a 5670 with a very similar hardware conf. As owner, have you noticed other issues like unusual ram usage, freeze,visual problem during movies (also hd movies) or normal pc use? Thank you in advance.

---

### Post by ejn114 on 2010-08-16
> **mantaor said:**
> Enj thanks for your experience, i wish to buy a 5670 with a very similar hardware conf. As owner, have you noticed other issues like unusual ram usage, freeze,visual problem during movies (also hd movies) or normal pc use? Thank you in advance.

Since getting the fglrx drivers installed and updated, everything is working fine.  I haven't noticed any unusual RAM usage, freeze, or problems during video playback at all.

---

### Post by mantaor on 2010-08-16
thanks a lot, surely I'll buy a 5670!!

---

