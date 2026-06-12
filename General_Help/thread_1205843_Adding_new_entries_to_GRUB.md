---
title: "Adding new entries to GRUB"
date: 2009-07-06
forum: General Help
---

### Post by desperateone on 2009-07-06
I just installed PC-BSD alongside Ubuntu and Windows, and I'd like to add it to GRUB boot menu. How would I do that? I'm not really good at this stuff, I'd just like the code to paste into menu.lst.

```
[~]: sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091ca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1352        7833    52066665    7  HPFS/NTFS
/dev/sda2            7834       13707    47182905   83  Linux
/dev/sda3           13708       14593     7116795    f  W95 Ext'd (LBA)
/dev/sda4               1        1351    10851592+  a5  FreeBSD
Partition 4 does not end on cylinder boundary.
/dev/sda5           13708       13968     2096451   82  Linux swap / Solaris
/dev/sda6           13969       14593     5020281    b  W95 FAT32

Partition table entries are not in disk order

```

---

### Post by hyperdude111 on 2009-07-06
```
sudo gedit /boot/grub/menu.lst
```

Add this to the bottom of the document.

>  title		PC BSD
root		(hd0,3)
makeactive
chainloader	+1


That would work for a windows like OS and it should also work for others. 

Where it says hd0,3 it could also be hd0,4 try both.

---

### Post by synapsys on 2009-07-06
FreeBSD is on sda4 which would be hd0,3

sda 1..2..3..4
hd0 0..1..2..3

hd0,4 would be sda5 which is swap

---

### Post by Jebtrix on 2009-07-06
Its going to be more like:

title  PC-BSD
root   (hd0,d)
kernel /boot/loader

Better explanation here:
[http://www.cyberciti.biz/tips/configure-ubuntu-grub-to-load-freebsd.html]("http://www.cyberciti.biz/tips/configure-ubuntu-grub-to-load-freebsd.html")

---

### Post by desperateone on 2009-07-06
> **hyperdude111 said:**
> ```
sudo gedit /boot/grub/menu.lst
```

Add this to the bottom of the document.



That would work for a windows like OS and it should also work for others. 

Where it says hd0,3 it could also be hd0,4 try both.

It worked, thank you.

---

