---
title: "General question regarding mount."
date: 2011-01-14
forum: General Help
---

### Post by MrWestwood on 2011-01-14
How do I go about mounting a device if I don't know the file system type (e.g ext3, NTFS)?

---

### Post by Habeouscorpus on 2011-01-14
mount /dev/<device>

It doesn't matter about the format. To check the device name, go to the disk utility. (You can even mount it there, too!)

---

### Post by pl@yer on 2011-01-14
Just leave off the -t for fstype. Or run fdisk /devicename to see what fs it is.

---

### Post by Habeouscorpus on 2011-01-14
mount /dev/<device>

It doesn't matter about the format. To check the device name, go to the disk utility. (You can even mount it there, too!)

---

### Post by Habeouscorpus on 2011-01-14
mount /dev/<device>

It doesn't matter about the format. To check the device name, go to the disk utility. (You can even mount it there, too!)

---

