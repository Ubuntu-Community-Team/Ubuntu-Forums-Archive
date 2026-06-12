---
title: "How to fix filesystem/superblock error?"
date: 2010-03-07
forum: General Help
---

### Post by rocknrollmouse on 2010-03-07
Running ubuntu server (ie no gui) but suspect this might be a general problem.

With the machine booted from the hard drive, if I run fdisk -l I get an invalid partition table message

> sudo fdisk -l

Disk /dev/hda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       48388   388676578+  fd  Linux raid autodetect
/dev/hda2           48389       48641     2032222+  fd  Linux raid autodetect

Disk /dev/md0: 398.0 GB, 398004715520 bytes
2 heads, 4 sectors/track, 97169120 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 2080 MB, 2080899072 bytes
2 heads, 4 sectors/track, 508032 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table


If I boot using gparted live CD, the drive information shows:
> Warning:

e2label: No such file or directory while trying to open /dev/md126p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.41.9 (22-Aug-2009)
dumpe2fs: No such file or
directory while trying to open /dev/md126p1

Unable to read the contents of this file system!
Because of this some operations may be unavailable.


How do I correct this error?

*(Not sure if this is related, but this machine periodically gives out a series of beeps high-low-high-low-high-low, not sure if this is related but I would like to get to the bottom of this as well* {I haven't put this in a separate post encase it is related to the above error.}*)*

---

### Post by patchwork on 2010-03-07
Try correcting the errors by running fsck from the live cd

---

### Post by rocknrollmouse on 2010-03-07
Just for the newbie in me:

Is there a limit to the number of consective times fsck can be ran?

Should I run fsck or e2fsck?

---

### Post by bumanie on 2010-03-07
Run this code in terminal via a live cd. Operating off a live cd will ensure the filesystem you are checking is unmounted. > sudo e2fsck -C0 -p -f -v /dev/sdxxEnsure you insert the drive letter and number instead of xx. Hope this helps.

---

### Post by rocknrollmouse on 2010-03-07
Many thanks Patchwork and Bumanie,

I've now ran e2fsck command as recommended by bumanie twice, (with a re-boot to hard drive in-between), but the results are the same as originally posted.

Is there an additional step I need to do to repair or recreate the superblock?

---

### Post by patchwork on 2010-03-07
I'm not sure if you'll be able to recreate the superblock, but this link shows how to turn the journaled filesystem to ext2 so that you can recover the data:

[http://www.unix.com/unix-advanced-expert-users/78965-linux-ext3-superblock-recovery.html](http://www.unix.com/unix-advanced-expert-users/78965-linux-ext3-superblock-recovery.html)

Sorry I couldn't be of more help

---

### Post by rocknrollmouse on 2010-03-11
Other than the Superblock error, the server is working fine, and all users have full access to data with no problems.

I've no idea how long the server has been running like this, but it maybe some time.  From reading the link posted by patchwork, *many thanks for that by the way*, it sounds like if I were able to recover a saved copy of the Superblock, then there is the risk (likelihood) of loosing data created after the corruption.  Clearly on a live server this isn't an option(!).  However there appears to be a way by stopping and re-starting journalling.

Please can someone confirm that I have the correct command sequence I need to stop and re-create the journal:
[LIST=1]
[*]Stop journalling:[FONT="Courier New"]           tunefs -O /dev/md0[/FONT]
[*]Check, and fix any errors:[FONT="Courier New"]  fsck -f /dev/md0[/FONT]
[*]Re-enable journalling:[FONT="Courier New"]      tunefs -j /dev/md0[/FONT]
[*]Check Superblock is fixed:[FONT="Courier New"]  e2fsck -n /dev/md0[/FONT]
[*]Optimise file system:[FONT="Courier New"]       tune2fs -O dir_index[/FONT]
[*]Add directory indexing[FONT="Courier New"]      e2fsck -f -D /dev/md0[/FONT]
 (speeds up file location in directories)
[/LIST]
 OK, last two steps aren't necessary, but seem to make sense whilst we have the server down for filesystem repair.

One question that comes to mind from the above, when we stop and re-start journalling, does this in itself clear the journal, or is there an extra command needed?

---

