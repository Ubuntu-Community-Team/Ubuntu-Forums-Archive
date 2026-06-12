---
title: "using live CD to ghost between hard drives"
date: 2006-01-29
forum: General Help
---

### Post by bpiadm on 2006-01-29
After partitioning the new hard drive and mounting both the original hard drive and the new one, we tried within GPARTED, I think, to copy the partition from the original HD to the new one.  On menu, COPY and PASTE were grey, inaccessible.  We got COPY to go from grey to black (accessible) by unmounting the original drive.  When we go to the new drive, PASTE stays grey and inaccessible, even when we try unmounting it.  

How, please, do you ghost original hard drive's contents to new hard drive?

---

### Post by lamego on 2006-01-29
If you want to clone a drive which only includes ntfs partitions the best thing to use is ntfsclone, try man ntfsclone.
If you want to clone an entire hd which has several partititions and they have the exact same size you can use the "dd" command.
For example if you have two IDE HDs named /dev/hda and /dev/hdb it should be something like.

sudo dd if=/dev/hda of=/dev/hdb
This will copy data from hda to hdb.

Please note that it will copy the ENTIRE hard disk, and I am assuming both disks have the exact same size.

**BE SURE YOU KNOW YOUR DISKS DEVICE NAMES**, if you do a mistake dd **will destroy **the wrong disk data without prompting !

---

### Post by bpiadm on 2006-01-29
Looking forward to giving that a shot.  Appreciate your answering that.

---

