---
title: "Attempting to format mp3 player / USB flash drive"
date: 2009-10-08
forum: General Help
---

### Post by ejn114 on 2009-10-08
Hi,

I have a Cowon S9 32GB mp3 player, and Ubuntu is mounting the player as read-only now because the filesystem (FAT32) has become corrupted.  I'd like to format the player to solve this problem (copying all my music is a minor inconvenience, but better than bricking the player).

The device is mounted as sdb1.  I tried using GPartEd to format the whole thing as FAT32 (which is what it should be, and already is...) but the operation failed.  The error message was "/dev/sdb: unrecognised disk label".  This then prompted me to make a new partition table, and I chose the default msdos table.  It showed the device as unallocated, so I attempted to create a FAT32 partition on the whole disk.  It failed at the step of creating the filesystem, giving the error "mkdosfs: unable to open /dev/sdb1".  Now the device is showing up twice in the file browser; one is unmountable, and the other is the device, still with all my data, as it was before.  How can I solve this problem and wipe the device?

Thanks.

---

### Post by Carl Hamlin on 2009-10-08
> **ejn114 said:**
> Hi,

I have a Cowon S9 32GB mp3 player, and Ubuntu is mounting the player as read-only now because the filesystem (FAT32) has become corrupted.

There are a number of directions in which this could go, all of which are entirely dependent upon *how* it became corrupted. What happened?

---

### Post by kanikilu on 2009-10-08
This might be a dumb question, but did you unmount the partition (but obviously keep the device plugged in) before trying to format?

[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-unmount-partition](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-unmount-partition)

---

