---
title: "Accessing the HD in FAT32"
date: 2006-05-17
forum: General Help
---

### Post by Last_Hero on 2006-05-17
My HD is partitioned in the FAT32 format, I have just managed to get Ubuntu to work and I hope you can tell me a way to access the files stored on my other partitions as my XP is currently a bit broken and refuses to aknowledge its existence.

Any programs that are bundled with Ubuntu able to help me?

Or do I have to DL them on my desktop and transer it to my laptop?

---

### Post by Ramses de Norre on 2006-05-17
Try [this]("http://ubuntuguide.org/#automountfat"), they tell you about ntfs too.

---

### Post by Last_Hero on 2006-05-17
I have a partion showing up now (yay) but its either the wrong one or I've lost all my data.

Thanks for the link Ramses

---

### Post by Ramses de Norre on 2006-05-17
Make sure you've got the wright device node. /dev/xxyz: 

xx: hd for ide disks or sd for sata disks 

y: first ide master: a, first ide slave: b, second ide master: c, second ide slave: d.
Sata: a,b,c,d for first, second, third.. sata controller.

z is a number to determine which partition on the disk, start counting from 1.

So the third partition on the first ide slave would be /dev/hdb3.

---

### Post by Last_Hero on 2006-05-17
I only have one hard disk, but my laptop has was pretty mucked up today because of a partition error. It wouldn'y load and I had to reinstall Ubuntu and tried to recover XP but my recovery disks didn't work -.-

I tried the name for all the partitions that the partition list thing said had to do with windows, apart from the first partition, cause I know thats XP, and not my data. One of them is extended though, so I just got an error.

---

