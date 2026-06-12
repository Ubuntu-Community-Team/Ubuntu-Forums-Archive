---
title: "Renaming other OS Partition"
date: 2011-09-17
forum: General Help
---

### Post by UltraZone on 2011-09-17
I have a few other OS installed side by side, and I would like to rename how they appear in the side pane of Nautilus (plus how they appear in Places, Shortcuts on GLX Dock, etc).  A purely cosmetic request is all this is.  Anybody know?

---

### Post by drs305 on 2011-09-17
On my system, the partitions under the Devices section show their 'label' names.

For linux partitions (ext2/3/4), you can do it from the terminal with:
```
sudo tune2fs -L *name* /dev/sd*XY*
```

You can also use Gparted or Disk Utility (Edit Filesystem Label) to create the label names. Gparted and Disk Utility can handle non-Linux partitions.

---

### Post by papibe on 2011-09-17
You can also edit the names on 'Disk Utility'.

Select the drive on the left, then the partition on the right. In the bottom right will be an option called 'Edit File SystemLabel'.

Hope it helps,
Regards.

---

### Post by UltraZone on 2011-09-18
Sweeet!!  Thanks guys that was easy!

---

### Post by papibe on 2011-09-18
> :p  Mark the thread solved when you have the chance.

Regards.

Oops, you did it before even wrote this.

---

