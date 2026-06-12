---
title: "Partition external hard disc"
date: 2006-01-30
forum: General Help
---

### Post by StefanoCole on 2006-01-30
Hello. I have an external hard disc containing only one big FAT32 partition. I use the hard disc with Ubuntu and, sometimes with Windows XP (dual boot system).
I'd like to shrink the FAT32 partition and, in the free space obtained, to create an ext3 partition to use only with Ubuntu. I'd like to know if it is possible to perform such partitioning operations with the Ubuntu Breezy live CD and the GParted application contained in the CD.

Thank you, Stefano

---

### Post by ockertom on 2006-01-30
mate what I can understan, ubuntu can read write to fat 32, all you have to do is mount the drive using the ubuntu disk proggy in admin. Dont format it, make a folder like fat32 and mount it in there. then enable it that should work.

---

### Post by StefanoCole on 2006-01-31
I have created a new ext3 partition on my external hard disc with GParted. The problem now is that the owner of the new volume is root. So, I am not able to read/write in it. From terminal I tried:

sudo chown stefano:stefano /media/usbdisk

But still the owner of  the volume remains root (I can check this from the property tab) and I am not able to write in it.

Help please, Stefano

---

