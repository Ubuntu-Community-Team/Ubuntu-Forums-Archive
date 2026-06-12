---
title: "Restore"
date: 2011-06-29
forum: General Help
---

### Post by bcl1713 on 2011-06-29
Here's the rub...
I have a laptop with a bum CD-Drive that won't boot from a usb key. It was running 10.10 quite nicely for me (installed before the drive went bad) but when I upgraded it to 11.04 over the internet a LOT of stuff broke.  No wifi, screen resolution, etc.  I should have anticipated this.  Anyway.. I have a usb drive and can make a "bootable" drive out of it.  Is there anyway from the recovery console (available from grub) or otherwise to wipe this machine and do a fresh install if I can't boot it directy from anything? Ugh.  help?

---

### Post by varunendra on 2011-06-30
If you USB drive is a USB Hard drive from which the laptop can (it should) boot, then it's quite easy to make a fresh install of your earlier working version. Since you said you "can make a bootable drive out of it", I assume you have access to another working computer.

[LIST]
[*]Make a fat32 partition of size 700MB or more on the usb (hard)drive,
[*]make it (only the fat partition) live bootable just like you would a usb key. CAUTION: Make sure to choose the FAT partition when installing live system on it, or else the whole drive may be reformatted.
[*]boot the laptop with it and proceed with installation.
[*]When the step to install GRUB occurs during installation, make sure your laptop's internal drive is selected as destination, not the USB drive. (However even if this mistake happens, it can be corrected later, but will need unnecessary extra efforts)
[/LIST]
Hope it all goes easy.

---

