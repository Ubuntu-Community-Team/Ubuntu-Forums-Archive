---
title: "Removing a partition"
date: 2006-03-27
forum: General Help
---

### Post by mempf on 2006-03-27
I had two linux partitions one for dapper and one for breezy. I want to remove the breezy partition and then resize the dapper partition to take up the free space.

How can I do this?

Thanks

---

### Post by lorenco on 2006-03-27
Are you familiar with parted ???

you can run :
sudo parted /dev/hda (or whatever your disc is)

then type ? and enter...

p- show partitions
you can resize the partitions:
"resize the filesystem on partition to start at start  and end at end megabytes":-D

---

### Post by lorenco on 2006-03-27
ps.  Y not keep one for later.  6.10 ??

---

### Post by mempf on 2006-03-27
[QUOTE=lorenco]ps.  Y not keep one for later.  6.10 ??[/QUOTE]

I need the space

---

### Post by justleen on 2006-03-27
Gparted works fine as well, if you preffer a GUI
available through apt

---

