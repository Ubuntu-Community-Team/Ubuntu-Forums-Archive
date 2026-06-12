---
title: "Errors after formatting 16GB flash drive"
date: 2010-06-08
forum: General Help
---

### Post by epiphanius on 2010-06-08
Hello:

After formatting a current batch of about 12 Kingston 16GB usb flash drives, I have to run an fsck an almost all of them, before I am able to mount them.

I formatted about 9 of these previously, on the same system, without these errors. 

I was using gparted originally, and  I switched to the command line. Now I get the errors whichever way I do the formatting. To troubleshoot, I have started by using fdisk to delete the default (fat32) partition, and create a new (linux) one. I am then doing:
mkfs -t ext2 /dev/sdb1.

My question is: is this a bad batch of drives, or are there some switches for mkfs that I could use to improve matters.

Here is the output from the repair process.

/dev>ls |grep sdb
brw-rw----   1 root   disk        8,  16 2010-06-08 15:32 sdb
brw-rw----   1 root   disk        8,  17 2010-06-08 15:36 sdb1
/dev>sudo e2fsck -f /dev/sdb1    
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Group descriptors look bad... trying backup blocks...
Resize inode not valid.  Recreate<y>? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #0 (31294, counted=31295).
Fix<y>? yes

Free blocks count wrong (3838129, counted=3838130).
Fix<y>? yes


Br13A: ***** FILE SYSTEM WAS MODIFIED *****
Br13A: 11/977280 files (0.0% non-contiguous), 70886/3909016 blocks
/dev>

Thanks for any help you can provide.

e.

---

