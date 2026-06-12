---
title: "uninstall windows 7 from dual boot ?"
date: 2011-07-27
forum: General Help
---

### Post by geordiejohn on 2011-07-27
hello i installed windows 7 ultimate 64 bit alongside Ubuntu 11.04 on my Acer Aspire 5536 but now i want to get rid of Windows,i have got the dvd for Ubuntu and i can reinstall but is there an easier way please?
thank you.

---

### Post by lrgmmc on 2011-07-27
so you have multiple partitions? one for windows one for ubuntu. if there is nothing on windows just delete the window partition and update grub to remove the entry.
what does ```
sudo fdisk -l
``` give you?

---

### Post by geordiejohn on 2011-07-27
i put your command in and get this-  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       24380   195727815+   7  HPFS/NTFS
/dev/sda3           24380       60802   292553729    5  Extended
/dev/sda5           24380       60443   289672192   83  Linux
/dev/sda6           60443       60802     2880512   82  Linux swap / Solaris

what do i do now please ?

---

### Post by lrgmmc on 2011-07-27
ok it looks like you have two windows partitions. was windows preinstalled? if there is nothing on either windows partition you can delete them using fdisk. ```
sudo fdisk /dev/sda
``` then it will give you a menu. enter d then it will ask for partition number enter 1 then do it again and enter 2. finally enter w. that will remove the two windows partitions.

---

### Post by geordiejohn on 2011-07-27
i think it may be best for me to do a clean install.
thank you.

---

### Post by lrgmmc on 2011-07-27
ok. best of luck.

---

