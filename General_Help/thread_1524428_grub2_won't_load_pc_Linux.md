---
title: "grub2 won't load pc Linux"
date: 2010-07-05
forum: General Help
---

### Post by garyed on 2010-07-05
I'm trying to figure out if this is a Grub2 issue or a PC Linux issue.
I have 3 HD's ;  2 ide & 1 sata
First IDE is Windows XP
Second IDE drive I have Ubuntu 9.10, 7.10 & PC Linux loaded
the SATA drive is FAT32 , just data 

In my grub.cfg it shows all my Linux OS's on (hd1,x) but the only one that doesn't load is PC Linux on (hd1,8)
The weird thing is if I create a custom menu & set PC Linux on (hd2,8) then it loads fine. 

I know that my 7.10 Ubuntu lists my HD's different than 9.10 because the 7.10 menu.lst uses (hd2,x) to load so I can't figure out why would PC Linux not work without customizing?
Just curious

---

### Post by oldfred on 2010-07-05
Is grub2 in the sda or sdb drive? I find that if I boot sdc my sda drive is drive 1 not drive 0 as I would expect if it is sda. It seems the boot drive becomes hd0 no matter what the drive order.

---

### Post by garyed on 2010-07-05
> **oldfred said:**
> Is grub2 in the sda or sdb drive? I find that if I boot sdc my sda drive is drive 1 not drive 0 as I would expect if it is sda. It seems the boot drive becomes hd0 no matter what the drive order.
Grub2 is on sdb6 & on the MBR of sda.

heres my fdisk> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6079    48829536   83  Linux
/dev/sdb2            6080       19457   107458785    5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris
/dev/sdb6            6080       12158    48829504+  83  Linux
/dev/sdb7           18182       18700     4168836   82  Linux swap / Solaris
/dev/sdb8           12159       18181    48379716   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)


As you can see all my Linux OS's are on sdb & grub only has a problem with PCLinux on sdb8. For some reason it won't load unless I set root = (hd2,8) & yet grub sets all the Linux OS's to (hd1,x) & the two Ubuntu's work fine.

---

