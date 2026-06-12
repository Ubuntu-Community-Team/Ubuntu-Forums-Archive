---
title: "Filesystem integrity problem"
date: 2012-04-07
forum: General Help
---

### Post by limonadovi on 2012-04-07
Hi All,

I have a strange problem on an old computer (Athlon XP 2400+ with 10G and 40G ATA HDs). Gsmartcontrol reports the HDs healthy, no sector relocation or surface defect during extended test.

I have installed Ubuntu Desktop 11.10 with ext4 filesystem, after it Ubuntu Desktop 10.04 with ext4, after the same with ext3, and all have the same problem:

Installation goes fine, and If i do a read only filesystem check on mounted partition, it gives 

```

root@bamer:~# e2fsck -n /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda1 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 51300 has zero dtime.  Fix? no
...

```some other orphaned inode, wrong block count etc errors follow.

However, if I do it from a live CD as here (now on an other, unmounted partition) to repair the errors, everything seems fine:

```

root@bamer:~# e2fsck -nf /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 230986/2321984 files (0.1% non-contiguous), 1772321/9277184 blocks

```altough the errors are there. If I do ```
touch /forcefsck
``` the next boot error check result is the same. I have already noticed some package failure due to these filesystem errors.

Have you seen something similar? What can I do (apart of buying new computer)?

thank you in advance.
Best regards: Balázs Bámer

---

### Post by dcstar on 2012-04-08
> **limonadovi said:**
> Hi All,

I have a strange problem on an old computer (Athlon XP 2400+ with 10G and 40G ATA HDs). Gsmartcontrol reports the HDs healthy, no sector relocation or surface defect during extended test.

I have installed Ubuntu Desktop 11.10 with ext4 filesystem, after it Ubuntu Desktop 10.04 with ext4, after the same with ext3, and all have the same problem:

Installation goes fine, and If i do a read only filesystem check on mounted partition, it gives 
..........

You **cannot** - repeat **cannot** - do a fsck on a mounted filesystem.

There is no "problem" with your system, only with its user.

---

### Post by limonadovi on 2012-04-08
Thank you, but you could have been a little more polite. Noone borns as fsck expert. I have found the explanation:
However, even if it is safe to do
so, the results printed by e2fsck are not valid if  the  filesystem  is
mounted.    If e2fsck asks whether or not you should check a filesystem
which is mounted, the only correct answer is ``no''.  Only experts  who
really know what they are doing should consider answering this question
in any other way.

---

