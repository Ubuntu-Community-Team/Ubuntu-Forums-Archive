---
title: "Lost partition"
date: 2010-01-20
forum: General Help
---

### Post by r_s on 2010-01-20
Well I deleted my hard disk , where I had a triple boot of vista, ubuntu and kubuntu after hours of work , I was not able to recover my ubuntu partition and lost everything .Now I need to recover some  of my partitions .I am running a live cd
the output of fdisk -l is 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+   6  FAT16
/dev/sda2              25        4202    33559785    c  W95 FAT32 (LBA)
/dev/sda3            9759       22596   103110656    7  HPFS/NTFS
/dev/sda4           22596       38914   131078839+   f  W95 Ext'd (LBA)
/dev/sda5           22596       28340    46134268    7  HPFS/NTFS
/dev/sda6           28341       28602     2104472   82  Linux swap / Solaris
/dev/sda7           28603       31520    23438800   83  Linux
/dev/sda8           31521       31861     2739040   82  Linux swap / Solaris

Now someone please help me to use parted to rescue my partition , gparted shows the enitre disk as unallocated.
I need quick assistance

---

### Post by davec64 on 2010-01-20
Have a look at TestDisk:

[http://http://www.cgsecurity.org/wiki/TestDisk]("http://http://www.cgsecurity.org/wiki/TestDisk")

It's in the Repositories.

I found it good for recovering partitions/data although I don't think it supports ext4 yet. :)

---

### Post by r_s on 2010-01-20
This is the output of fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+   6  FAT16
/dev/sda2              25        4202    33559785    c  W95 FAT32 (LBA)
/dev/sda3            9759       22596   103110656    7  HPFS/NTFS
/dev/sda4           22596       38914   131078839+   f  W95 Ext'd (LBA)
/dev/sda5           22596       28340    46134268    7  HPFS/NTFS
/dev/sda6           28341       28602     2104472   82  Linux swap / Solaris
/dev/sda7           28603       31520    23438800   83  Linux
/dev/sda8           31521       31861     2739040   82  Linux swap / Solaris

Now whenever I run parted and print anything it says 
Can't have a partition outside the disk! 
This is becuase for /dev/sda4 it shows end as 38914 while I have only 38913 sectors .So anybody please help me to fix this usnig fdisk, cause I am really nervous this time...

---

### Post by r_s on 2010-01-20
Please help me to use parted to recover my lost partition, it always says 
Error: Can't have a partition outside the disk!

---

### Post by phillw on 2010-01-20
Hi,
for a well thought out & written 'How To' on your problem, I'd recommend heading over here --> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Regards,

Phill.

---

### Post by mk1w86 on 2010-01-20
Have you tried TestDisk?  When you say parted I assume you mean Gparted? :confused: 

EDIT: Just looked at link above and am guessing you don't. :oops:

---

### Post by r_s on 2010-01-20
Well sorry for that, I'll explain my problem in a greater detail.
Initially I had a triple boot of vista, kubuntu and ubuntu , I deleted my ubuntu partition accidentally then I tried to recover it using testdisk (from kubuntu)  but messed up and I was left with grub error: No device found. (I found out that I had wiped off my entire hd as unallocated)

I booted using a live ubuntu cd and checked the output of fdisk -l (which I already posted) ..now I wanted to recover my lost partition  so I thought of using GNU parted (rescue )  as I had already messed up with testdisk once. But when I start it using "sudo parted /dev/sda" it gives an error   
 Error: Can't have a partition outside the disk!         
That is the problem I'm facing , any suggestions.

---

