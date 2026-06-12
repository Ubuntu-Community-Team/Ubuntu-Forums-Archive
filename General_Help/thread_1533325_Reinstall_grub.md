---
title: "Reinstall grub"
date: 2010-07-17
forum: General Help
---

### Post by Kangarooo on 2010-07-17
PC1 had drives
a with grub and ubuntu 9.04
b ubuntu distro 9.04 w/o grub

now i want drive b in PC2
but since it doesnt have grub then how can i get it in drive b?
i can put drive b in PC3 witch has drive c with grub 2 and xubuntu 10.04
maybe from it i can also make drive b bootable?

---

### Post by oldfred on 2010-07-17
From a liveCD,  just be sure to follow the directions for old grub:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you can boot into the install in your drive just reinstall grub from that to sdb, if it is sdb.

This is to refresh your GRUB files in /boot/grub and re-install GRUB to MBR.
sudo grub-install /dev/sdb
This is to automatically generate a new menu.lst file for you.
sudo update-grub

---

