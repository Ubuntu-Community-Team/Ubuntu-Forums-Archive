---
title: "gparted frozen"
date: 2011-02-08
forum: General Help
---

### Post by mtrobey on 2011-02-08
I'm trying to use GParted from a liveusb to resize my ext4 Ubuntu partition, but it's been stuck on the "shrink file system...resize2fs" for two days straight.  The progress bar is still going back and forth, and top shows a lot of CPU activity, but it won't move past this point.  I know it's a bad idea to stop GParted while it's resizing, but does anyone have any ideas for what I can do, maybe a way to check to see if it's actually busy resizing the partition?

---

### Post by srs5694 on 2011-02-08
How big is the partition (or was it before you began)? Also, were you resizing by moving the start or the end of the partition? Also, what interface does the disk use (SATA, PATA, USB, etc.)? A 2-day resize is plausible for certain answer to these questions, such as a really big partition resized from the start on a USB interface. A 2-day resize is excessive, and probably means the program has hung, for other answers, such as a 10 GiB partition resized from the end on an SATA or PATA disk.

---

