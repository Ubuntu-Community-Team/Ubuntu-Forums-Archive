---
title: "Where is my openSolaris..."
date: 2009-07-17
forum: General Help
---

### Post by B07030810 on 2009-07-17
I devided my harddisk to 3 primary partion ,I install XP in the first one ,Solaris in the sencond,finally...I install ubuntu int the third ...before I installed ubuntu,it woks correctly...When I start the computor ,the grub menu show I can choose the solaris ,windows,solaris in text mode,But,after I install ubuntu....The Solaris is missed !In the grub menu,I can see only ubuntu and windows !My ubuntu is 8.04.. What's wrong ...How did it happen ...How can I fix it ...

---

### Post by nikhilk on 2009-07-17
Could you post the output of ```
sudo fdisk -l
``` and the contents of your "/boot/grub/menu.lst" file?

---

### Post by B07030810 on 2009-07-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf1a2f26

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3227    25920846    7  HPFS/NTFS
/dev/sda2            3228        6415    25607610   bf  Solaris
/dev/sda3            6416        9600    25583512+  83  Linux
/dev/sda4            9601        9729     1036192+   f  W95 Ext'd (LBA)
/dev/sda5            9601        9729     1036161   82  Linux swap / Solaris



Here it is ...How can I do ....

---

### Post by nikhilk on 2009-07-17
Could you also post contents of your "/boot/grub/menu.lst" file?
```
sudo cat /boot/grub/menu.lst
```

---

### Post by B07030810 on 2009-07-18
Thank you .I have solved my my problem.It seems to be that ubuntu can't recongnized Solaris.I edit the menu.lst in ubnutu adding the Solaris ,then it's fixed.Thank you all the same~~

---

### Post by nikhilk on 2009-07-20
> **B07030810 said:**
> Thank you .I have solved my my problem.It seems to be that ubuntu can't recongnized Solaris.I edit the menu.lst in ubnutu adding the Solaris ,then it's fixed.Thank you all the same~~

Great, glad to hear that! You are welcome :)

---

