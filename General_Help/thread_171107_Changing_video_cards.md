---
title: "Changing video cards"
date: 2006-05-05
forum: General Help
---

### Post by kop316 on 2006-05-05
Hello everyone

Recently I got a PCI Radeon 9200 video card (which amazingly enough is a step up form wut i currently use). When I installed it, everything loaded up fine until i got to the GDM, in which it said it would not display propperly. WHen I looked at the output, it said that it is still trying to output to my old video card (which is onbaord the motherboard).

How to I switch it to the new video card without having to reinstall my system?

---

### Post by bluevoodoo1 on 2006-05-05
from a terminal type "lspci" and find the BusID of your new card.

here's an example of my lspci relating to my video card...

0000:02:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)


then...

sudo dpkg-reconfigure xserver-xorg

when you get to the screen where it asks for the BusID, type in your new one.

---

### Post by tseliot on 2006-05-05
Boot in Recovery mode (you can choose it from the GRUB menu almost as soon as you turn on your computer)

then type:
```
dpkg-reconfigure -phigh xserver-xorg
```

The Xserver should AUTOMATICALLY detect your new card.

Then type:
reboot

---

