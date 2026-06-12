---
title: "Formatting a disk drive"
date: 2006-05-02
forum: General Help
---

### Post by Mike Landon on 2006-05-02
Hello,

I have a simple question:

How do I prepare an empty hard disk on my kubuntu 5.10 system.

I have tried the following:

fdisk /dev/hda

successfully created partition 1

then:

mkfs -t ext3 /dev/hda1

but get:

mke2fs 1.38 (30-Jun-2005)
/dev/hda1: Invalid argument passed to ext2 library while setting up superblock

Help please :)

---

### Post by Titus A Duxass on 2006-05-02
If you are doing this prior to an install it's much easier to run the install process, partitioning is one of the steps.

---

### Post by Mike Landon on 2006-05-02
I have already installed kubuntu. Need to do the format on 2 disks which weren't formatted during installation.

---

### Post by mibadt on 2006-05-02
May I suggest using the (graphical) QTParted.
Either download and install it, or, easier, get a Knoppix CD, boot it and ran QTParted (included in Knoppix).

Take Care
;)

---

### Post by trotski on 2006-05-02
I've had my best luck using cfdisk.

---

### Post by bonefishchris on 2006-05-03
erm... shouldn't you be formatting hdb (and c) rather than hda?

---

