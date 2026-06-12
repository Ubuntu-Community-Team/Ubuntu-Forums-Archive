---
title: "running fsck on the root filesystem."
date: 2010-09-19
forum: General Help
---

### Post by melrokz on 2010-09-19
Is it possible to run fsck on the root file system?
My Ubuntu 10.04 seems to be checking it's fs at boot...
It shows that the file system is in use and can get severely damaged!
Or the only possibility is to run it from a live CD?

---

### Post by yetiman64 on 2010-09-19
> Is it possible to run fsck on the root file system?Yes.
By using the code
```
sudo touch /forcefsck
```you can have fsck check ALL filesystems, including root, on the next boot up. The blank file created will be automatically removed by fsck prior to subsequent boot ups.

Note, that it is not a good idea and I believe may actually cause some problems, if you try to run fsck on a mounted filesystem, hence your noticing filesystem checking being done at boot time (before the filesystems are mounted).

---

### Post by garvinrick4 on 2010-09-19
> **melrokz said:**
> Is it possible to run fsck on the root file system?
My Ubuntu 10.04 seems to be checking it's fs at boot...
It shows that the file system is in use and can get severely damaged!
Or the only possibility is to run it from a live CD?
Do not run fsck on a mounted drive(one that is in use)
Use a live Cd (install CD and use TRY Ubuntu)
Open a terminal in live cd and
```
sudo e2fsck /dev/sdx
```The x being whatever your partition # is you want to run fsck on. sda1, sda2 sda5 ect. ect.
Get your sda # by.
```
sudo fdisk -l 
```( small case L)

---

