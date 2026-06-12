---
title: "filesystem errors that can not be fixed"
date: 2011-11-16
forum: General Help
---

### Post by Nick42 on 2011-11-16
Hello,

I have Ubuntu 11.04 installed on my desktop HP Pavillion Elite HPE-515sc. Product information is here: [http://tinyurl.com/5srv769](http://tinyurl.com/5srv769)

Recently I started to see mysterious "free space warnings" even though I should have quite many GBs free. I checked free space and certainly there was no big files added recently that would change the free space significantly.

Then I ran fsck and saw that there were filesystem errors. I ran "touch /forcefsck" and in the next reboot I had free space back.

Though free space problem solved, something strange is not resolved yet. When I run "fsck -nfv /dev/sda5", I get errors which you can find at the end of this post. No matter I type "touch /forcefsck" and reboot, those errors don't go away. 

I also tried Ubuntu Live CD but then fsck did not find any errors!

What can I do now?

PS: /dev/sda5 is a logical ext4 partition.

Thanks in advance for help!

Here's the output of "fsck -nv /dev/sda5"

fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Warning!  /dev/sda5 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 1572883 was part of the orphaned inode list.  IGNORED.
Inode 1572885 was part of the orphaned inode list.  IGNORED.
Inode 2622445 was part of the orphaned inode list.  IGNORED.
Inode 2626550 was part of the orphaned inode list.  IGNORED.
Inode 2626967 was part of the orphaned inode list.  IGNORED.
Deleted inode 3542240 has zero dtime.  Fix? no

Inode 3542294 was part of the orphaned inode list.  IGNORED.
Inode 3542404 was part of the orphaned inode list.  IGNORED.
Inode 3542496 was part of the orphaned inode list.  IGNORED.
Inode 3542522 was part of the orphaned inode list.  IGNORED.
Inode 3542526 was part of the orphaned inode list.  IGNORED.
Inode 3542534 was part of the orphaned inode list.  IGNORED.
Inode 3542594 was part of the orphaned inode list.  IGNORED.
Inode 3542595 was part of the orphaned inode list.  IGNORED.
Inode 3542602 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(3311104--3311138) -(14360106--14360111) -(14360123--14360129) -(14360133--14360148) -14360157 -(22613117--22613119) -(22613138--22613145) -(22616155--22616167)
Fix? no

Free blocks count wrong (18835981, counted=18835390).
Fix? no

Inode bitmap differences:  -1572883 -(1572885--1572886) -1572916 -2622445 -2626550 -2626967 -3542240 -3542294 -3542404 -3542496 -3542522 -3542526 -3542534 -(3542594--3542595) -3542602
Fix? no

Free inodes count wrong for group #192 (3918, counted=3916).
Fix? no

Free inodes count wrong (5787804, counted=5787713).
Fix? no


/dev/sda5: ********** WARNING: Filesystem still has errors **********


  249700 inodes used (4.14%)
     491 non-contiguous files (0.2%)
     371 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 212781/98/3
 5285619 blocks used (21.91%)
       0 bad blocks
       4 large files

  170042 regular files
   31546 directories
      59 character device files
      26 block device files
       0 fifos
     402 links
   48061 symbolic links (36766 fast symbolic links)
      31 sockets
--------
  250167 files

---

### Post by matt_symes on 2011-11-16
Hi

Your running fsck on a mounted read/write file system ?

> Warning!  /dev/sda5 is mounted.If you are then don't!!!!! 

Trust the output from the LiveCD where the only partitions that get automounted on your hard drive are the swap partitions.

When run on a mounted read/write partition the filing is lightly to be in an inconsistent state when running the check due to caching etc.

Kind regards

---

### Post by Nick42 on 2011-11-16
Yes, the errors are retrieved only when I run it on a mounted drive.

So, basically, even errors could be bogus in that case? Strange that they even allow it run then, if errors could be bogus.

---

### Post by matt_symes on 2011-11-16
Hi

> **Nick42 said:**
> Yes, the errors are retrieved only when I run it on a mounted drive.

So, basically, even errors could be bogus in that case? Strange that they even allow it run then, if errors could be bogus.

Linux will let you do loads of crazy things to your system if you want :) If you run fsck without the -N option it will warn you that you are doing something very daft but it will not stop you doing it if you so desire.

The errors are not bogus in so much as the filing system on the disk - when mounted - can be in an inconsistent state due to caching and other effects. The kernel and the drive will write out the data to the disk when the disc is unmounted or the OS shut down correctly; disc syncing (there are other times this can occur as well).

See

```
man sync
```

fsck will only check the data written on the disc and will not know if the kernel or hard drive has decided it is not going to write all its data to the disk until a later point.

All is well as long as the OS is shut down cleanly and fsck runs on an unmounted partition.

Kind regards

---

### Post by Nick42 on 2011-11-16
Thanks Matt!

My (non)problem is solved then :)

BTW, for reference there's also good information here:
[https://lists.ubuntu.com/archives/ubuntu-users/2010-November/234930.html](https://lists.ubuntu.com/archives/ubuntu-users/2010-November/234930.html)

---

