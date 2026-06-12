---
title: "Getting files off HD. Rewrote partition table."
date: 2010-01-28
forum: General Help
---

### Post by JesterDev on 2010-01-28
Long story short I have windows 7 installed and in an attempt to install ubuntu the existing partition table was erased. What's the safest method to mount an ntfs partition and back up files? Or even write a table to get back into windows to back files up?

---

### Post by Leppie on 2010-01-28
try testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
```
sudo apt-get install testdisk
sudo testdisk
```

good luck

---

### Post by efflandt on 2010-01-28
If you manage to restore your partitions, the best way to shrink Win7 partition is to use administration tools in Win7 itself.  Then create whatever partition(s) you want for Linux with gparted, and tell Ubuntu installation specifically which existing partition(s) to use during installation (without any auto resizing).

I tend to shy away from any automatic partitioning, since years ago 64-bit WinXP beta messed up my partition table geometry (changed heads/cyls, so it could not even boot itself).  After I fixed that with fdisk from a Linux rescue CD (no data loss), I saw that SuSE (from figures it revealed before acting) was about to do the same thing.

---

