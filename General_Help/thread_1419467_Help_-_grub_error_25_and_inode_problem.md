---
title: "Help - grub error 25 and inode problem"
date: 2010-03-01
forum: General Help
---

### Post by peter011 on 2010-03-01
Hi

yesterday, i was browsing then my computer froze and i had to restart it the hard way. On reboot i got a error message saying Grub error 25. i read all about the error and did some investigation. i found that my hdd partition hosting my system isntallation (ubuntu) is unreadable. I think there is a inode problem in my disk. Here's the result of my investigation.
```
ubuntu@ubuntu:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): q

ubuntu@ubuntu:~$ ls -l dev/disk/by-id
ls: cannot access dev/disk/by-id: No such file or directory
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf41e91c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       38913   234420480    f  W95 Ext'd (LBA)
/dev/sda5            9730       19448    78067836    7  HPFS/NTFS
/dev/sda6           19449       29181    78180291    7  HPFS/NTFS
/dev/sda7           29182       38913    78172258+   7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd2fd124

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            6644       19929   106719795    f  W95 Ext'd (LBA)
/dev/sdb2               1        6643    53359866   83  Linux
/dev/sdb5            6644       13286    53359866    7  HPFS/NTFS
/dev/sdb6           13287       19929    53359866    7  HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo fsck -f/dev/sdb2
fsck 1.41.4 (27-Jan-2009)
ubuntu@ubuntu:~$ sudo e2fsck -cd -p -f -v /dev/sdb2
/dev/sdb2: Superblock has an invalid journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

Error reading block 1057 (Attempt to read block from filesystem resulted in short read).  

/dev/sdb2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo e2fsck -cd -f -v /dev/sdb2
e2fsck 1.41.4 (27-Jan-2009)
Error reading block 1057 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes

Force rewrite<y>? yes

Resize inode not valid.  Recreate<y>? yes

badblocks: Input/output error during ext2fs_sync_device
Checking for bad blocks (read-only test): done                                
/dev/sdb2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Programming error?  block #1024 claimed for no reason in process_bad_block.
Root inode is not a directory.  Clear<y>? no

Error reading block 1064 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? no

Error reading block 1072 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? no

Error while scanning inodes (128): Can't read next inode
e2fsck: aborted


```

[[IMG]http://img706.imageshack.us/img706/7088/p1020723n.th.jpg[/IMG]](http://img706.imageshack.us/i/p1020723n.jpg/)

the sdb2 is the ubuntu instalation and it look broken.

what should i do to recover my emails from thunderbird?

thx a lot

---

