---
title: "doesnt boot anymore, kernelpanic in repairmode"
date: 2011-11-18
forum: General Help
---

### Post by Mappenz on 2011-11-18
Hi,

I locked my screen, when i wanted to log in again the screen kept black. Now my laptop wont reboot anymore. 
I was logged in as root and building glibc when this occoured. My OS is Ubuntu 11.04, now i am using ubuntu 11.11 live cd.

I would prefer to repair my old sytem with the settings i made.

regards
Michi

---

### Post by Mappenz on 2011-11-18
```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 364022/18497536 files, 4050191/73973877 blocks
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   591793063   295895508   83  Linux
/dev/sda2       621092862   625141759     2024449    5  Extended
/dev/sda3       591802470   612911879    10554705   83  Linux
/dev/sda4       612911880   621088964     4088542+  82  Linux swap / Solaris
/dev/sda5       621092864   625141759     2024448   82  Linux swap / Solaris

Partition table entries are not in disk order

```

is it usefull information, that table entries are not in disc order

---

### Post by Mappenz on 2011-11-19
Hi,

i still didnt find a simple solution. I will now try to burn a 11.04 live CD and look if there is a repairfunction. If not successful I will try to upgrade to 11.10. Any comments?

kind regards
Michi

---

### Post by raja.genupula on 2011-11-19
I am unable to figure out the issue actually . 
Issue seems some what complex , this time i can say is backup imp data and re install the  Ubuntu.

---

### Post by Mappenz on 2011-11-21
I looked at the output when booting in repairmode again. It says something about segfault and libc. When the last thing before I did was building glibc. I was pretty sure to build and install it on a different partition but maybe I didn't.

Is there a chance to fix a broken glibc?

---

### Post by alphaamanitin on 2011-11-21
Had the same problem with 9.10.  Ended up having to do a complete reinstall.  good luck.

AlphaA

---

### Post by Mappenz on 2011-11-21
Did you build glibc too?

---

### Post by alphaamanitin on 2011-11-22
Nope.  Just a default install of Ubuntu with almost nothing else installed from the software center, let alone building anything.  That is why I didn't mind breaking down and having to do a reinstall.

AlphaA

---

