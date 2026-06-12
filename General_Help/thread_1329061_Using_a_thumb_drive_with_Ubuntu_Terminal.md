---
title: "Using a thumb drive with Ubuntu Terminal"
date: 2009-11-17
forum: General Help
---

### Post by dgohn on 2009-11-17
In a terminal session, how would one go about saving a file onto a thumb drive.  I know how to mount the cdrom devices but I can't seem to figure out how to mount the thumb drive.

Thanks in advance

---

### Post by neilengineer on 2009-11-17
1. plug in your thumb drive
2. $sudo fdisk -l     you'll find a new disk like sda/sdb
3. mount your drive with something like: mount /dev/sda1 /mnt
4. copy your file to /mnt
5. umount /mnt

---

### Post by dgohn on 2009-11-17
When I go to mount it it is telling me:

mount:  You must specify a filesystem type

Any ideas?

Thanks

---

### Post by dgohn on 2009-11-17
bump

its fat16 file system also

---

