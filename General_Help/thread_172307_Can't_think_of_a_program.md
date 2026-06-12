---
title: "Can't think of a program"
date: 2006-05-08
forum: General Help
---

### Post by Sonique on 2006-05-08
Doesnt anyone know of a program that can recover corrupt partitions in ubuntu?  I have no clue of where to find one.
Cheers

---

### Post by exosyst on 2006-05-08
Can you define corrupted?
Is it an ext2/3 issue? Are you wanting to repair a linux or windows partition? What happened to cause the problem?

---

### Post by Sonique on 2006-05-08
It is a ntfs partition, grub wont boot it even though it is listed there. Also in ubuntu I cannot view it even if I edit my fstab file to make it supposedly viewable, I just came to the assumtion the drive is corrupted.

---

### Post by Irony on 2006-05-08
Post your;

[PHP]sudo fdisk -l[/PHP]

See if it corresponds to what is shown in gparted;

*System Tools > GParted*

---

