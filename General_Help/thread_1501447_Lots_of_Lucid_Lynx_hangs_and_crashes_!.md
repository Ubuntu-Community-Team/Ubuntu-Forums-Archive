---
title: "Lots of Lucid Lynx hangs and crashes !"
date: 2010-06-04
forum: General Help
---

### Post by trintin7 on 2010-06-04
I'm getting a lot of hangs crashes even Kernel Panic from using 10.04.
Originally I use 9.10 then upgrade to 10.04. It was fine at first until I have RAM problem (I have 512x2) so I have to take one of them out because it was corrupted.
After that the problem erupted.

When I use Chrome to watch YouTube (using latest Flash). It start to slows the computer down and end up hang.
Another case, Running Warcraft III The Frozen Throne 1.24e on Wine the computer crashes during load (this problem exist since I have 1GB RAM. Warcraft used to work fine when I use 9.10)
Lastly, frequent Kernel Panic during boot this happen when ubuntu do disk error check.

If anyone have the same problem or found a way to solve this Please Share

HP Pavilion dv2018tx
CPU:Intel(R) Core(TM)2 CPU T5600  @ 1.83GHz
RAM:1 Kingston 512MB DDR2(used to have two)
HDD:WDC WD3200BEVT-1
GPU:GeForce Go 7200 128 MB 200 MHz PCI-E 16x


Thanks in Advance !

---

### Post by dino99 on 2010-06-04
your problem is mainly due to ram (only 512 Mo) and using heavy config and apps: choose either more ram or xfce or lxde instead of gnome, and be sure that your video driver is well activated.

---

### Post by trintin7 on 2010-06-04
Well I turned the effects off and the drivers are correct and latest.And about the RAM problem when I replace the corrupted one with the good one from another computer the problem is still exist.

---

### Post by dino99 on 2010-06-04
anything into logs ?

clean the system:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

open synaptic repo, and check you only use genuine lucid repo (no third party or ppa), then update and install gconf-cleaner 

sudo apt-get install -f
sudo dpkg --configure -a

goto: apps system gconf-cleaner: run it (yes to all)

---

