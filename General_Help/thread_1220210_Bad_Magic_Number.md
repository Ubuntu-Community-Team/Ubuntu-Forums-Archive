---
title: "Bad Magic Number"
date: 2009-07-22
forum: General Help
---

### Post by I Use Dial on 2009-07-22
I have two 250 GB SATA drives not in a RAID that have the error 'Bad Magic Number'.

I ran xfs_repair and it was unable to validate a backup superblock.

I have not formatted nor repartitioned the drives.

From the last time the drives were working I:

Tried to reinstall Ubuntu 8.04 onto the 60 GB PATA drive and had received a GRUB error 21 (or 25? twentysomething)

Then reinstalled 8.04 again and found that something was wrong with my mobo and I couldn't see both of the two new 1 TB SATA drives I found it was an issue on my old mobo BIOS.

Installed Windows XP and proceeded to screw up the BIOS flash (first time ever, I swear).

So now with new mobo everything is fine for the most part except this little problem when I run dmesg:

> XFS: bad magic number
SB validate failed
XFS: bad magic number
SB validate failed

When I look at the drives in GParted it shows they still have like 40 or 70 GB of free space, which is about where they should be with the data on them.

Anything I can do to recover the information on the drives?  It appears still intact...

---

