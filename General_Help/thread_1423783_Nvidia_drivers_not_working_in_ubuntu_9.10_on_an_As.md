---
title: "Nvidia drivers not working in ubuntu 9.10 on an Asus ul80vt laptop"
date: 2010-03-07
forum: General Help
---

### Post by jateenjoshi on 2010-03-07
I have an Asus UL80vt laptop. This laptop has an integrated (Intel) as well as a discrete (Nvidia 210m) graphics card.

I want to use the nvidia proprietary drivers because from what I understand, it's the easiest way to set up dual monitors (I have an external monitor). I installed the latest nvidia driver: NVIDIA-Linux-x86-190.53. When I try to run the NVidia X Server Settings GUI, it tells me that "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I checked out my xorg.conf and changed the device driver to 'nvidia' instead of 'nv'. Curiously, when I run nvidia-xconfig, it changes the intel device to 'nvidia' which is a problem. So i skipped running that and just stuck with my xorg.conf. When I run startx, I get a message saying "failed to initialize the NVIDIA graphics device PCI:1:0:0". 

I've combed through multiple forums which state different kinds of solutions and I've tried different kernel options such as 'vmalloc=512m' or 'noapic' to no avail. I'm at my wit's end here, and any help would be much appreciated. :)

P.S. I've attached my xorg.conf file

---

### Post by jateenjoshi on 2010-03-09
Noone? Bumping thread

---

### Post by MuzYka on 2010-03-09
Have the same problem. So far only succeeded to switch off nvidia card from power compiling a module to do that (useful to run on battery).
When failing with nvidia, the Xorg.0.log reports that "screens found" but not those which nvidia could use.

---

### Post by MuzYka on 2010-03-09
Maybe it is not just supported, at least there is no G210M in this list
[ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.16/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.16/README/appendix-a.html)

---

### Post by elkoko on 2010-09-26
Hi, I was able to make the Nvidia card to work by setting in the bios the SATA mode to compatible (instead of enhanced). It sunds bizarre but works :P, But still haven't figured out how to make it work while the hdd is used as sata instead of IDE. Can Someone help? Excuse my english. Thanks

---

