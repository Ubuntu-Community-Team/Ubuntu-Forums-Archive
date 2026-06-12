---
title: "random files are incorrectly reported as &gt;5TB large.  What is ruining my file system?"
date: 2011-09-30
forum: General Help
---

### Post by the Goat on 2011-09-30
I have a weird problem that I can't figure out.  On my data partition (mdadm raid5 with ext4 file system) I have found several files that 'ls -l' and 'stat' report as having a HUGE size (>5TB).  They are not supposed to be anywhere near that size and 'du' reports the correct (smaller) size.

The files appear inaccessible.  The only fix I've found is to just delete them.  So far this has only affected some mp3 files (which I re-ripped as flac) and some random pictures.

Any ideas how I can fix these files and prevent more from forming?

*Output from the relevant commands. . .*
```

ryan@htpc:/alpha/download$ ls -l BNM487.jpg
-rwxrwxrwx 1 ryan ryan 5264384339968 2009-12-10 02:24 BNM487.jpg


ryan@htpc:/alpha/download$ stat BNM487.jpg
  File: `BNM487.jpg'
  Size: 5264384339968   Blocks: 9120       IO Block: 4096   regular file
Device: 10301h/66305d   Inode: 8155884     Links: 1
Access: (0777/-rwxrwxrwx)  Uid: ( 1000/    ryan)   Gid: ( 1000/    ryan)
Access: 2011-09-29 23:33:56.666542271 -0400
Modify: 2009-12-10 02:24:07.966982391 -0500
Change: 2011-04-24 15:11:13.492166001 -0400


ryan@htpc:/alpha/download$ du BNM487.jpg
4560    BNM487.jpg

```

---

### Post by dcstar on 2011-09-30
> **the Goat said:**
> I have a weird problem that I can't figure out.  On my data partition (mdadm raid5 with ext4 file system) I have found several files that 'ls -l' and 'stat' report as having a HUGE size (>5TB).  They are not supposed to be anywhere near that size and 'du' reports the correct (smaller) size.

The files appear inaccessible.  The only fix I've found is to just delete them.  So far this has only affected some mp3 files (which I re-ripped as flac) and some random pictures.

Any ideas how I can fix these files and prevent more from forming?
.........

Have you done a fsck on the array?

---

### Post by the Goat on 2011-09-30
> **dcstar said:**
> Have you done a fsck on the array?

Affirmative.  I should have included that.  I have unmounted the partition and run fsck on it.  No errors were reported.

---

### Post by the Goat on 2011-09-30
Just to cover all my bases I did another fsck so I could post the output.  It looks clean. . .

```

ryan@htpc:/var/log$ sudo fsck -vf /dev/md0p2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

 1982209 inodes used (0.81%)
   67594 non-contiguous files (3.4%)
     948 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 1/0/0
         Extent depth histogram: 1915241/64849/1271
910260356 blocks used (93.19%)
       0 bad blocks
     110 large files

 1946581 regular files
   34759 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
     860 symbolic links (838 fast symbolic links)
       0 sockets
--------
 1982200 files

```

---

