---
title: "Howto fix errors on disk"
date: 2010-01-24
forum: General Help
---

### Post by vdings on 2010-01-24
I have errors on my disk would appreciate some assistance on how to eliminate the errors.

Here is the output 

```
sudo e2fsck -nfv /dev/sda6
e2fsck 1.41.9 (22-Aug-2009)
Warning!  /dev/sda6 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 109 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 3090 was part of the orphaned inode list.  IGNORED.
Inode 8751 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -279192
Fix? no

Inode bitmap differences:  -109 -3090 -8751
Fix? no

Free inodes count wrong for group #0 (1, counted=0).
Fix? no

Free inodes count wrong for group #1 (2, counted=1).
Fix? no

Free inodes count wrong (2177751, counted=2177749).
Fix? no


/dev/sda6: ********** WARNING: Filesystem still has errors **********


  136057 inodes used (5.88%)
     160 non-contiguous files (0.1%)
      98 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 114870/20
  878723 blocks used (9.50%)
       0 bad blocks
       1 large file

   93851 regular files
   15240 directories
      68 character device files
      26 block device files
       2 fifos
     388 links
   26795 symbolic links (20995 fast symbolic links)
      65 sockets
--------
  136435 files

```

---

### Post by dcstar on 2010-01-24
> **vdings said:**
> I have errors on my disk would appreciate some assistance on how to eliminate the errors.

Here is the output 

```
sudo e2fsck -nfv /dev/sda6
e2fsck 1.41.9 (22-Aug-2009)
Warning!  /dev/sda6 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 109 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 3090 was part of the orphaned inode list.  IGNORED.
Inode 8751 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -279192
Fix? no

Inode bitmap differences:  -109 -3090 -8751
Fix? no

Free inodes count wrong for group #0 (1, counted=0).
Fix? no

Free inodes count wrong for group #1 (2, counted=1).
Fix? no

Free inodes count wrong (2177751, counted=2177749).
Fix? no


/dev/sda6: ********** WARNING: Filesystem still has errors **********


  136057 inodes used (5.88%)
     160 non-contiguous files (0.1%)
      98 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 114870/20
  878723 blocks used (9.50%)
       0 bad blocks
       1 large file

   93851 regular files
   15240 directories
      68 character device files
      26 block device files
       2 fifos
     388 links
   26795 symbolic links (20995 fast symbolic links)
      65 sockets
--------
  136435 files

```

Boot off a Live CD and manually run fsck on the partition. **Never** run fsck on a mounted partition.

---

### Post by vdings on 2010-01-24
Is there a way to force e2fsck to run at boot?

I tried touch /forcefsck, and that runs fsck but I am not sure if fsck can fix problems on an  ext4 file system.

Regards

---

### Post by vdings on 2010-01-24
Please help, how do i check my file system for errors without creating a start up disk, its insane that there is no way to do this.

---

