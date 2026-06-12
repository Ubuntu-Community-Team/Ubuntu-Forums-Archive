---
title: "Ubuntu not loading, stuck at &quot;busybox&quot;"
date: 2012-08-12
forum: General Help
---

### Post by ubuntu27 on 2012-08-12
Hello in one of my laptops, ubuntu is not loading anymore. Instead when it tries to load, it lands in "busybox".

```
BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shall (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I am running a live xubuntu 12.04 right now, and when I opened the file browser to acces my hard drive, I noticed that the Linux partition is gone. I can only access the windows partition. But interestengly, the windows partition shows twice in the thunar.

But Ubuntu partition does show up in fdisk.


When I open or acces the partition it says:

> Failed to mount "79 GB Filesystem".
Error mounting: Mount: Wrong fs type, bad option, bad superblock on /dev/sda5,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so

```
xubuntu@xubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x122cd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154417151    77208544+   7  HPFS/NTFS/exFAT
/dev/sda2       154419198   312580095    79080449    5  Extended
/dev/sda5       154419200   308520959    77050880   83  Linux
/dev/sda6       308523008   312580095     2028544   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c2fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
xubuntu@xubuntu:~$ 

```

```
xubuntu@xubuntu:~$ dmesg | tail
[ 5311.128139] Descriptor sense data with sense descriptors (in hex):
[ 5311.128145]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 5311.128169]         0d ba 12 31 
[ 5311.128180] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 5311.128194] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 0d ba 12 20 00 00 f0 00
[ 5311.128217] end_request: I/O error, dev sda, sector 230298161
[ 5311.128299] ata1: EH complete
[ 5311.128366] JBD2: Failed to read block at offset 14920
[ 5311.128397] JBD2: recovery failed
[ 5311.128406] EXT4-fs (sda5): error loading journal

```


Thank you in advence. :)

---

### Post by drs305 on 2012-08-12
It's possible there are errors on the Ubuntu partition which are preventing it from being read. You can check by booting a LiveCD and running the following commands. Do not mount the partition.

If the first command finds errors, run the second command, which will attempt to fix them:

```
sudo e2fsck -C0 -p -f -v /dev/sda5  
# if errors:
sudo e2fsck -f -y -v /dev/sda5
```

---

### Post by ubuntu27 on 2012-08-12
Thank you for your help drs305.
This is what I got:

```
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Clearing orphaned inode 1183769 (uid=1004, gid=1004, mode=0100644, size=40960)
/dev/sda5: Clearing orphaned inode 1183752 (uid=1004, gid=1004, mode=0100600, size=69632)
/dev/sda5: Clearing orphaned inode 3803262 (uid=1004, gid=1004, mode=0100600, size=4096)
/dev/sda5: Clearing orphaned inode 1050745 (uid=1004, gid=1004, mode=0100600, size=12288)
/dev/sda5: Clearing orphaned inode 1050744 (uid=1004, gid=1004, mode=0100644, size=16384)
/dev/sda5: Clearing orphaned inode 1048724 (uid=1004, gid=1004, mode=0100600, size=12288)
/dev/sda5: Clearing orphaned inode 1048748 (uid=1004, gid=1004, mode=0100644, size=16384)
                                                                               
  349202 inodes used (7.25%)
    2553 non-contiguous files (0.7%)
     636 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 305779/428
10474900 blocks used (54.38%)
       0 bad blocks
       1 large file

  254475 regular files
   40473 directories
      59 character device files
      26 block device files
       0 fifos
     404 links
   54126 symbolic links (42866 fast symbolic links)
      34 sockets
--------
  349597 files
xubuntu@xubuntu:~$ 

```

**EDIT:** I restarted, and...
Super! It worked! THANK YOU SO MUCH!!1

Say, if it is not too much trouble, could you explain what that command did?

---

