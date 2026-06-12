---
title: "img file"
date: 2009-09-22
forum: General Help
---

### Post by saskatchewan on 2009-09-22
Ubuntu 8.11 ASUS eee1000 easypeasy

I want to upgrade to Ubuntu 9.04 on my netbook.  I downloaded the img file from the ubuntu site but, I don't know how to put it on to a usb.

Also, could I put it on to a SD rather than a usb?

Thanks

---

### Post by anaconda on 2009-09-22
the manual command to copy the image to an usb stick (or SD card):
```

sudo dd if=/path/to/your/downloaded.img of=/dev/device/you/saw/in/dmesg bs=1M 

```
This command is typed to terminal.

Jus change the 
if=to the path to your input file... Probably something like
if=/home/yourName/Desktop/filename.img
and 
of= to the devicename you want it to be copied. On my setup it would be:
/dev/sdb
(You dont want to put the number after the sdb)

if you dont know what is the devicename to your SD-card you can type:
sudo fdisk -l 
and from the output of that command you should be able to read where it is.

ANd I think it will work jus as well from SD-card, because I THINK the internal SD-reader in asus is just a normal usb-SD reader.

PS. if you have problems. There is also an alternative graphical program for doing the same. The name of it is probably imagewriter or something..

---

### Post by prem1er on 2009-09-22
> **anaconda said:**
> 
PS. if you have problems. There is also an alternative graphical program for doing the same. The name of it is probably imagewriter or something..

Yep, If you can't get that to work, try Unetbootin.  It downloads and installs the distro of your choice right on a USB. It also makes it bootable automagically!

---

### Post by saskatchewan on 2009-09-22
The output I got is as follows, but I am not sure which is the SD card.
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef196

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

Disk /dev/sdc: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1204     1920955+   6  FAT16

---

### Post by anaconda on 2009-09-22
> **saskatchewan said:**
> The output I got is as follows, but I am not sure which is the SD card.
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x294a294a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 32.2 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef196

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3924    31519498+  83  Linux

Disk /dev/sdc: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1204     1920955+   6  FAT16

I would say the SD-card is /dev/sdc1 , because the size of it is ~2GB (and the filesystem type is FAT, whic is widely used in memory sticks and cards).

the other drives are: 8GB and 32GB, which both have linux filesystems, and it seems that your 8GB is the bootable one.... You should know what size your sd-card is....

But remember to use /dev/sdc (and not /dev/sdc1  sdc1 is the first and only partition of your SD-card, and sdc is the card, whic is what dd wants as an argument.. )

And it might be best to unmount the sd-card before copying the image to it. 
sudo umount /dev/sdc1

---

### Post by saskatchewan on 2009-09-22
thanks, I will try your suggestions.

---

### Post by saskatchewan on 2009-09-27
solved!!

---

