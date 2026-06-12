---
title: "hard disk partitioning"
date: 2010-11-18
forum: General Help
---

### Post by donpeter06 on 2010-11-18
I tried to install ubuntu 10.10 in my amd PC.
but during the partition selection it showed my entire hard disk as free space. I had partitioned my hard disk into 3 . 2 NTFS and 1 FAT32 partitions, I dont know what to do to  continue my installation. i have window 7 installed in one of the partition. 
please help. Thanx:popcorn:

---

### Post by dino99 on 2010-11-18
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by donpeter06 on 2010-11-18
thanx for the help.
Why do u think the Ubuntu partition manager did not detect any of m other partitions?>
when i live boot with the CD i am able to view all 3 of my partitions but during installation the case is different as i told.

---

### Post by Mark Phelps on 2010-11-18
Sometimes the partition manager does not detect the partitions correctly.

To be safe, boot into a LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list ALL the partitions on your drive.  I would not be surprised to see that you actually have 4 primary partitions -- the maximum number allowed.

If that is the case, the installer can NOT install for you -- because it can not create any more partitions.

---

### Post by psusi on 2010-11-18
It does not detect the partitions because there is something broken with your partition table.  The output of fdisk -lu will show what is wrong.

---

