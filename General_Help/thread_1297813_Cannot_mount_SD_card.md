---
title: "Cannot mount SD card"
date: 2009-10-22
forum: General Help
---

### Post by anier on 2009-10-22
Hi. I'm a newbie here. I actually installed ubuntu 9.04 four days ago. There seems to be an error when I insert my SD card in the reader. The error says:

mount: /dev/mmcblk0p1 can't read superblock

What should I do? 

Thanks for helping.

---

### Post by tarps87 on 2009-10-22
Can you post the output of
```
fdisk -l /dev/mmcblk0p1
```
It sounds like the partition info is corrupt, is this a new card?

---

### Post by anier on 2009-10-22
No, it's not a new card. 

It says:

can't open /dev/mmcblk0p1

---

### Post by tarps87 on 2009-10-22
Can you try
```
sudo fdisk -l
```

Have you used this card on a windows machine?

---

### Post by tedrogers on 2009-12-26
I have this same problem and the (relevant) output for sudo fdisk -l is as follows:

```
Disk /dev/sdb: 495 MB, 495452160 bytes
255 heads, 63 sectors/track, 60 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e98fea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          60      481918+   6  FAT16
```

...nothing untowards there as far as I can tell...yet I still get this SUPERBLOCK error when I try and mount the SD card?

If I do "sudo mount -t vfat /dev/sdb1 /media/usb" I get this:

```
mount: /dev/sdb1: can't read superblock

```

...but why???? Hmmmm.

---

### Post by farrukh_najmi on 2012-07-20
I had the same "bad superblock" issue with my phones SD card. I used [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover the data from my disk. I then used gparted to delete the partition on the SD card and then recreate it. After that I copied the data I had recovered using TestDisk back to the SD card after mounting it normally.

[LIST]
[*] Most steps needed to done as root (TestDisk, gparted)
[*] gparted was install using: sudo apt-get install gparted
[*] gparted was run using: sudo gparted
[/LIST]

Not sure if I have a recurring problem on my SD card but so far it seems to be working. I will be sure to back it up more frequently now.

---

