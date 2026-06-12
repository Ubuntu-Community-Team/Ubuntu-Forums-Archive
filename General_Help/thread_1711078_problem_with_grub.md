---
title: "problem with grub"
date: 2011-03-20
forum: General Help
---

### Post by shakibv on 2011-03-20
Hi,
I wanted to test fedora 15 so I installed it on my system, and used fedora automatic installation I mean I just used the shrink the hard drive and use it's free space option and let the fedora decide the rest, but when the installation was over my ubuntu was gone, how can I add it to fedora's grub list again ?
thanks.

---

### Post by wilee-nilee on 2011-03-20
> **shakibv said:**
> Hi,
I wanted to test fedora 15 so I installed it on my system, and used fedora automatic installation I mean I just used the shrink the hard drive and use it's free space option and let the fedora decide the rest, but when the installation was over my ubuntu was gone, how can I add it to fedora's grub list again ?
thanks.

Post from the terminal 
fdisk -l

Identify what is what. You can just reload grub2 from the other install if there is one and it will boot everything without menu editing. Grub2 will chain load grub-legacy very nicely.

---

### Post by shakibv on 2011-03-20
this is my fdisk -l output :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076e0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   245762047   122880000   83  Linux
/dev/sda2       306442238   312580095     3068929    5  Extended
/dev/sda3       245762048   246786047      512000   83  Linux
/dev/sda4       246786048   306440191    29827072   8e  Linux LVM
/dev/sda5       306442240   312580095     3068928   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/vg_shakibpc-lv_swap: 2080 MB, 2080374784 bytes
255 heads, 63 sectors/track, 252 cylinders, total 4063232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_shakibpc-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/vg_shakibpc-lv_root: 28.5 GB, 28454158336 bytes
255 heads, 63 sectors/track, 3459 cylinders, total 55574528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_shakibpc-lv_root doesn't contain a valid partition table

---

### Post by wilee-nilee on 2011-03-20
Can you identify the actual installs, I'm trying to get you into the grub2 to reload it and back on the road. I'm assuming you have a install with grub2 it helps if confirm this stuff as fedora is grub-legacy I believe.

---

### Post by shakibv on 2011-03-20
yes,

---

### Post by wilee-nilee on 2011-03-20
> **shakibv said:**
> yes,

So I have to ponder why this has not been shared.

---

### Post by shakibv on 2011-03-20
> **wilee-nilee said:**
> So I have to ponder why this has not been shared.

srry :-( , would you please tell me how I can reload grub2 ?

---

### Post by shakibv on 2011-03-20
tnx :-), my problem solved, I just added the lines from old ubuntu grub to fedora's of course with little changes and it worked

---

