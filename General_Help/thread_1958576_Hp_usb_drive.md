---
title: "Hp usb drive"
date: 2012-04-14
forum: General Help
---

### Post by benj23673 on 2012-04-14
Ok, so my friend was goofing around with my laptop (looking for a encrypted file) and now it wont read my hp usb drive I dont exactly know what he did but the usb drive is not recognized on my windows or ubuntu drives anyway can someone help because I have no clue whats going on I would really like my files back if possible 

main@main-ThinkPad-E520:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b5811aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS/exFAT
/dev/sda2         3074048   397052089   196989021    7  HPFS/NTFS/exFAT
/dev/sda3       592371712   625139711    16384000   83  Linux
/dev/sda4       397053950   592371711    97658881    5  Extended
/dev/sda5       584167424   592371711     4102144   82  Linux swap / Solaris
/dev/sda6       397053952   584167423    93556736   83  Linux

Partition table entries are not in disk order

---

### Post by agillator on 2012-04-14
Look for the obvious first. Is the drive actually mounted? If so, where? I assume this is an external drive connected through a usb port?

---

### Post by benj23673 on 2012-04-14
its an 8gb flash drive and when it is plugged in nothing happens?

---

### Post by agillator on 2012-04-14
I'm still a little confused - not your fault. Disconnect the drive and run fdisk -l. Then connect it, wait a moment, and run fdisk -l again. Is there any difference?

---

### Post by callmemahavir on 2012-04-15
What is the filesystem of the pen drive ? 

Is your OS support that file system.

Refer this page...

[http://www.howtogeek.com/73178/what-file-system-should-i-use-for-my-usb-drive/](http://www.howtogeek.com/73178/what-file-system-should-i-use-for-my-usb-drive/)

IT GIVES LOT OF INFORMATION!!!

---

