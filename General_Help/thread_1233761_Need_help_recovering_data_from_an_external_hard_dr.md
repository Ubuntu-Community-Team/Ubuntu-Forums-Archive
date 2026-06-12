---
title: "Need help recovering data from an external hard drive"
date: 2009-08-07
forum: General Help
---

### Post by Zeroangel on 2009-08-07
Hey all,

I have an external hard drive which is formatted with 3 partitions:

Partition 1: Swap partition [swap]
Partition 2: Portable Linux Partition "FaunOS" [iso9660]
Partition 3: Shared files partition "Vanguard" [NTFS]

Partition 2 has a bootable linux distro loaded onto it which can save its running state using squashFS.

However after almost a year of use the OS has become unbootable. As a result i've been thinking of reformatting the partition using the stock OS image and then copying the session data (SQF files).

However, whenever I try to copy the SQF files to a folder on my ubuntu install, I get I/O errors which cause the copy operation to fail.

I ran the command
```
sdavid@icarus ~ $ sudo fsck /dev/sdc2             
fsck 1.41.4 (27-Jan-2009)                        
e2fsck 1.41.4 (27-Jan-2009)                      
FaunOS contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes              
Error reading block 334615 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 13.  Ignore error<y>? yes

Force rewrite<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts      
Pass 5: Checking group summary information
FaunOS: 52/10112 files (13.5% non-contiguous), 346361/2578828 blocks
```However, the files still do not copy over without I/O errors, and running fsck with sector checking will only get to 1.57% before it slows to an absolute crawl (as in, it would take half an hour just to go up a percentage)

I'm sure the hard drive is still good, as I can mount as well as read and write to the NTFS partition just fine.

Can anyone tell me how to fix the problems on the linux partition?

---

### Post by Zeroangel on 2009-08-07
*bump*

---

### Post by Zeroangel on 2009-08-09
*bump again!*

---

### Post by merlinus on 2009-08-09
You might try testdisk and photorec.

---

