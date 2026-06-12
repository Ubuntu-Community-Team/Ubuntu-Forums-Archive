---
title: "Formatting FAT32?"
date: 2005-01-22
forum: General Help
---

### Post by Kakalto on 2005-01-22
I have made a FAT32 partition on my system, and I'd like to put the filesystem on it, but I don't want to use the windows formatter, as I will possibly accidently format over linux. I have heard of a mkfs extension called dosfstools, which can put a filesystem of vfat onto a partition. However, I don't know exactly how to install it, and I am not sure if the debian version will work. Could someone please help me with this?

Thanks in advance,
Kakalto

---

### Post by Quest-Master on 2005-01-22
Just use parted. Start it up in the terminal (parted), and use the many available and easy-to-use options listed.

---

### Post by Viro on 2005-01-22
[QUOTE=Kakalto]I have made a FAT32 partition on my system, and I'd like to put the filesystem on it, but I don't want to use the windows formatter, as I will possibly accidently format over linux. I have heard of a mkfs extension called dosfstools, which can put a filesystem of vfat onto a partition. However, I don't know exactly how to install it, and I am not sure if the debian version will work. Could someone please help me with this?

Thanks in advance,
Kakalto[/QUOTE]
 You could use mkdosfs. Its probably the simplest way. Just do mkdosfs -F 32 */dev/partition* and you're set!

---

### Post by az on 2005-01-22
man mkfs.vfat #(or mkdosfs)


They are the same thing.

---

### Post by Kakalto on 2005-01-23
Heheh, I used the dosFStools, and formatted vfat, but it was fat16!

Anyways, I just rebooted into the ubuntu installation cd, went into expert mode, and skipped everything up to partitioning hard disk, and formatted that partition FAT32, then ended my install. 

Thanks for your help anyway, guys.

---

