---
title: "hard disk partition missing."
date: 2011-09-30
forum: General Help
---

### Post by niyazmurshed on 2011-09-30
Hello friends, 

i just installed ubuntu 11.10. i had 3 partitions in windows 7. 

when installing ubuntu , i made a new partition from one of them as ext4 (20gb) and swap for 4gb, everything is working fine.

but when i strtd win7, they arent showing my partitions in My computer.

Before installation.  C: 64gb  D: 120gb E: 120gb
after installing ubuntu  C: 64gb

how can i get back my partitions?? please, i lyk ubuntu.i dn want to uninstall it.can u please tel me how i can get it back???

---

### Post by An Sanct on 2011-09-30
Try going to Windows Disk Management. It looks like the one in the picture below.

[http://imageshack.us/photo/my-images/709/disks.png/sr=1](http://imageshack.us/photo/my-images/709/disks.png/sr=1)

And check if the disks are visible. Note, that Windows 7 does not (want to) see a Linux partition and where Linux is the label will say something like : "healthy, unformatted", twice (system and swap).

---

### Post by dcstar on 2011-09-30
> **niyazmurshed said:**
> Hello friends, 

i just installed ubuntu 11.10. i had 3 partitions in windows 7. 

when installing ubuntu , i made a new partition from one of them as ext4 (20gb) and swap for 4gb, everything is working fine.

but when i strtd win7, they arent showing my partitions in My computer.

Before installation.  C: 64gb  D: 120gb E: 120gb
after installing ubuntu  C: 64gb

how can i get back my partitions?? please, i lyk ubuntu.i dn want to uninstall it.can u please tel me how i can get it back???

How did you "make a new partition"?

---

### Post by niyazmurshed on 2011-09-30
when i booted from my usb to install ubuntu, they had this option for making partition.i made it from there.

---

### Post by dcstar on 2011-09-30
> **niyazmurshed said:**
> when i booted from my usb to install ubuntu, they had this option for making partition.i made it from there.

Possibly the Ubuntu installer offered you the option to overwrite the non-C: partitions and you did not read the relevant messages.

Unless you had existing free space on the disk then Ubuntu had to find space to install itself from somewhere.

---

