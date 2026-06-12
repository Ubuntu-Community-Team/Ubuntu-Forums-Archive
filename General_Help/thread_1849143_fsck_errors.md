---
title: "fsck errors"
date: 2011-09-23
forum: General Help
---

### Post by rbowen1 on 2011-09-23
I had a 60 gig Sata disk that I had loaded Ubuntu 11.04.   Starting having issues and eventually would not boot to the OS.   Still able to boot OK to another disk with Ubuntu 10.04.  I have been able to back up all data and am ready to reload Ubuntu but would like to do a bad blocks check on the drive in advance so that all bad blocks can be redirected before I load the OS.   

After doing some research, I found this** Ubuntu Brainstorm**:  Idea #6972: Ubuntu needs a tool for marking bad sectors of harddrives           link:  [http://brainstorm.ubuntu.com/idea/6972](http://brainstorm.ubuntu.com/idea/6972)

Ran this code:  sudo fsck -ccv /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

It looks like fsck wants to try to repair the file system.  I just want it to check for bad bocks and redirect them.   Load a fresh Ubuntu 10.04 on the disk.    

What switches should I specify to accomplish this task?

Thanks in advance.  Ubuntu rocks!

---

### Post by SeijiSensei on 2011-09-23
> **rbowen1 said:**
> It looks like fsck wants to try to repair the file system.  I just want it to check for bad bocks and redirect them.   Load a fresh Ubuntu 10.04 on the disk.

Brainstorm???  The tool to mark bad blocks has been around for over a decade.

Either run the badblocks utility, or perhaps better from your point of view, run 'mke2fs -t ext4 -c /dev/sdX'.  The "-c" switch invokes the badblocks checker during the formatting of the disk.  Adding a second "-c" makes it do a read/write test on each block.  This will take hours but will be more accurate.  See "man e2fsck" and "man badblocks" for details.

---

### Post by dcstar on 2011-09-24
> **SeijiSensei said:**
> Brainstorm???  The tool to mark bad blocks has been around for over a decade.

Either run the badblocks utility, or perhaps better from your point of view, run 'mke2fs -t ext4 -c /dev/sdX'.  The "-c" switch invokes the badblocks checker during the formatting of the disk.  Adding a second "-c" makes it do a read/write test on each block.  This will take hours but will be more accurate.  See "man e2fsck" and "man badblocks" for details.

Anyone using a disk with known bad blocks to try and load a **new** system deserves all the problems that they get.

I just hope that they don't come back here complaining about how "unreliable" their system is afterwards.

---

### Post by rbowen1 on 2011-09-24
> **SeijiSensei said:**
> Brainstorm???  The tool to mark bad blocks has been around for over a decade.

Either run the badblocks utility, or perhaps better from your point of view, run 'mke2fs -t ext4 -c /dev/sdX'.  The "-c" switch invokes the badblocks checker during the formatting of the disk.  Adding a second "-c" makes it do a read/write test on each block.  This will take hours but will be more accurate.  See "man e2fsck" and "man badblocks" for details.

I have been supporting computers for many years with a focus on Windows in the last decade.  Only turned to Linux/Ubuntu in the past year.   Still getting up to speed with Linux so I apologise if the questions seem elementary. 

Oddly smart disk data shows the drive to be healthy and it will now boot to the OS.   I have verified that the suspect disk has these three partitions now.   1. /dev/sdb1, main partition has 59 gig showing as type ext4          2. /dev/sdb2, Extended partition has 1.3              3. /dev/sdb5, Swap partition has 1.3

If I run the mke2fs -t ext4 -cc /dev/sdb1 (which I fully expect to take many hours),  will that data be saved to the disk smart data table and be used when I boot up with a install CD to load the fresh install? 

What if disk has an intermittent issue with one of the sectors in the extended or swap file area?

---

### Post by rbowen1 on 2011-09-25
Update to my original question about fsck error.    It appears that I was getting the error because I was running fsck on the entire disk:   fsck -ccv /dev/sdb.    When I ran it on just the main data partition, it ran (almost 4 hours) with no errors and found no bad blocks.   

sudo fsck -ccvp /dev/sdb1
[sudo] password for testy: 
fsck from util-linux-ng 2.17.2
 /dev/sdb1: Updating bad block inode.

  228450 inodes used (6.37%)
     484 non-contiguous files (0.2%)
     356 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 193405/82
 1536976 blocks used (10.73%)
       0 bad blocks
       1 large file

  155739 regular files
   27457 directories
      59 character device files
      26 block device files
       0 fifos
     400 links
   45154 symbolic links (34862 fast symbolic links)
       6 sockets
--------
  228841 files

*****************************************************************************************************

Can I run fsck on the swap partition?  if yes then what options?

---

### Post by SeijiSensei on 2011-09-25
No, just run the badblocks utility.  swap isn't a filesystem, and it isn't formatted.  "Formatting" swap by using the mkswap command just fills the partition with zeroes.  I believe it's equivalent to "dd if=/dev/zero of=/dev/sdX".

Running fsck against the entire device and not a partition with an installed filesystem will give you meaningless results.

---

