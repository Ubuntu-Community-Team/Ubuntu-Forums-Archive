---
title: "grub menu"
date: 2010-12-27
forum: General Help
---

### Post by mr.farenheit on 2010-12-27
i'm gonna completely remove my windows partition. when i delete it will i have to do anything to grub so it doesn't show up in the boot menu or will grub recognize the windows partition is gone and do it automatically?

---

### Post by Verbeck on 2010-12-27
you'll have to run *sudo update-grub* from a terminal

---

### Post by wilee-nilee on 2010-12-27
> **mr.farenheit said:**
> i'm gonna completely remove my windows partition. when i delete it will i have to do anything to grub so it doesn't show up in the boot menu or will grub recognize the windows partition is gone and do it automatically?

As long as the Ubuntu is not a wubi=being installed inside windows the last post is correct. If it is a wubi removing windows will remove Ubuntu as well.

---

### Post by mr.farenheit on 2010-12-28
good to know from both posts. i was planing on just running live image and just deleting the windows partition and in the same process move ubuntu and expand the partition with the remaining free space.

---

### Post by wilee-nilee on 2010-12-28
> **mr.farenheit said:**
> good to know from both posts. i was planing on just running live image and just deleting the windows partition and in the same process move ubuntu and expand the partition with the remaining free space.

If you use gparted and move the left side of the partition to the left, it will take a long time so be prepared for that. You may have to reinstall grub if you move the front end.

Many just put a partition there and make a separate home, or a storage partition.

---

