---
title: "Raid Array Failure"
date: 2010-08-12
forum: General Help
---

### Post by Cerin on 2010-08-12
I have a RAID-1 array running under Ubuntu 10.04. The Gnome Disk Utility is showing that the array is degraded, and that one is faulty, but both drives are also showing "healthy" status. How is this possible? I've tried "check array" to check and repair the drive, but it doesn't appear to do anything. Is there any way to confirm the faulty disk is fatally broken and requires replacement?

---

### Post by Ocxic on 2010-08-12
The S.M.A.R.T. status shows as HEALTHY(e.g.: the disk hardware itself).

The actual data/partitions/file system may be corrupted showing a DEGRADED status.

I would:
1: Backup all your data on the array. (just in case)
2: Erase/Format the supposed bad/failed disk
3: Rebuild the array with the erased/formated/new disk
4: If issue persists the Drive is bad. Replace drive, and repeat step 3.

---

