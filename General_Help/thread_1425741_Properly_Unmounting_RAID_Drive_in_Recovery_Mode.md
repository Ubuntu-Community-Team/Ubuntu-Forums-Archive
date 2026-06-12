---
title: "Properly Unmounting RAID Drive in Recovery Mode"
date: 2010-03-09
forum: General Help
---

### Post by DaveJL on 2010-03-09
Hi,

I had a corrupted superblock in my RAID boot drive (/dev/md0), which I fixed with fsck in Recovery Mode.

However, after rebooting, the same boot-up problem (hanging for hours) persists.

When I re-enter Recovery Mode to examine the boot drive, I found its superblock was corrupted again (which I fixed again using fsck).

Is there a proper reboot procedure which is gentle on the boot drive, such that it doesn't corrupt it?  Or, is something else amiss?

Thanks,
Dave

---

