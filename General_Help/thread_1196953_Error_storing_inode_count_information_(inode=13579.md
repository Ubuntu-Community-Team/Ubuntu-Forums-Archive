---
title: "Error storing inode count information (inode=135790848, count=53199): Memory allocati"
date: 2009-06-25
forum: General Help
---

### Post by daelus0 on 2009-06-25
Hey People,

I Lost a hdd out of a LVM.

I've replaced with a drive of the same size and manufacturer just a newer firmware version.

Now I'm running
```
fsck.ext3 -y -f -v /dev/mapper/Linuxbox-Shared
```after a few hours of running I get the following error.
```
Error storing inode count information (inode=135790848, count=53199): Memory allocation failed
e2fsck: aborted
```

Any Ideas what this means or now to fix it?

I've searched but all I can find is translation documentation.

---

### Post by daelus0 on 2009-07-12
Incase anyone else actually runs into this error in the future.

I ended up rebuilding the file system from scratch but then I also found I had another bad drive in my LVM and I suspect that was part of the issue.

So Try running some long smart tests on your drives. I found one that was failing with an abundant of DMA errors.

---

