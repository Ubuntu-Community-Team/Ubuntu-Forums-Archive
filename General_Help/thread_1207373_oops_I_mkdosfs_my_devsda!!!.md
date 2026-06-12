---
title: "oops I mkdosfs my /dev/sda!!!"
date: 2009-07-08
forum: General Help
---

### Post by bork on 2009-07-08
I did a bad thing and am in need of some desperate help. I am a long time user of Ubuntu but still a newbie when it comes to this sort of thing. I was trying to format my flash drive and instead of using /dev/sdc, I accidently changed my /dev/sda to an msdos partition leaving my system useless. Reading some of the forums, I downloaded the rescue disk and used "testdisk" which seemed to guess my old partitions. Once the new partition table was written, my sda mounts as a blank disk, though fdisk and other utilities still report the proper amount of free space and used space on the whole drive.  I tried to recover my data onto another internal drive using "ddrescue". It made the exact copy of the blank disk problem complete with partition tables and disk usage stats. My goal is to recover the data. Any ideas? 

Anybody's help is greatly appreciated!

---

### Post by miklcct on 2009-07-13
Try fsck /dev/sda1
(Although the beginning of the drive is located, you may still find alternate superblocks left)

---

