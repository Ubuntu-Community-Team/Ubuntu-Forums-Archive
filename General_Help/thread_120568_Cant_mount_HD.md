---
title: "Cant mount HD"
date: 2006-01-22
forum: General Help
---

### Post by TheSource on 2006-01-22
Im trying to mount this partition but ubuntu wont let me. Ive searched around and couldn't get anything to work.

This is the error:

> 
user@ubuntu:~$ sudo mount -t ext3 /dev/sda1/ /mnt/sda1/
Password:
mount: special device /dev/sda1/ does not exist
       (a path prefix is not a directory)


Yet it shows up with fdisk.

> 
root@ubuntu:/home/user# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             640        9351    69979108+  83  Linux
/dev/sda2            9352        9729     3036285    f  W95 Ext'd (LBA)
/dev/sda3   *           1         639     5132736   83  Linux
/dev/sda5            9352        9729     3036253+  82  Linux swap / Solaris



---

### Post by breakman on 2006-01-22
Try it without slashes at the end...
> sudo mount -t ext3 /dev/sda1 /mnt/sda1

---

### Post by TheSource on 2006-01-23
You gotta be joking..... lol. I'm such a tard.

---

