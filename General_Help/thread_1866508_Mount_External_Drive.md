---
title: "Mount External Drive"
date: 2011-10-21
forum: General Help
---

### Post by Howie Spitz on 2011-10-21
External drive connected with e-SATA,at first both partitions showed the correct mount point labels but I could not mount either. After rebooting I was able to mount the first partition but not the second so I ran Disk Utility's Check Filesystem which said partition not clean and now that ext3 partition is Unknown rather than labeled as before.External LaCie 500 GB HD and only a couple years old. What would be the best way to retrieve the files on this partition/ and then repair or check the drive/partition. Partition used to be /MOSTstuff.
 
:~$ cat /proc/partitions 
major minor  #blocks  name

 8       16  488386584 sdb
 8       17  104510826 sdb1
 8       18   82148377 sdb2


:~$ dmesg | tail
[  128.831066] ata8: hard resetting link
[  134.034063] ata8: softreset failed (device not ready)
[  134.034073] ata8: reset failed, giving up
[  134.034080] ata8.00: disabled
[  134.034110] ata8: EH complete
[  134.034247] sd 7:0:0:0: [sdb] Unhandled error code
[  134.034260] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  134.034276] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 41 00 00 02 00
[  134.034327] end_request: I/O error, dev sdb, sector 65
[  134.034445] EXT3-fs: unable to read superblock

What I want to do is mount the 84 GB Unknown Partition and copy the  files I have there.When I Analyzed with TestDisk it said Structure OK  but found no partitions. What would be the best way to proceed. fstab  and fdisk do not list this drive.
Thank you for help or advice.

---

### Post by Howie Spitz on 2011-10-22
Still can't mount external drive but I'm finding more info:
:~$ sudo blkid
/dev/sdb1: LABEL="/SHAREDstuff" UUID="79468041-196b-4175-94b5-3293465ef225" TYPE="ext3" 
/dev/sdb2: LABEL="/MOSTstuff" UUID="bad35c1b-b972-42c2-bf14-27f3b718e24c" SEC_TYPE="ext2" TYPE="ext3" 

sudo mke2fs -n /dev/sdb 
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30531584 inodes, 122096646 blocks
6104832 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

Should I try to copy files off the HD first. or try to use a different Superblock? Should I use Superblock backups for each partition or the whole drive? Thank you for any advice or help.

---

### Post by Howie Spitz on 2011-10-22
I mounted the external drive , though not exactly sure how. Changed SATA to IDE in BIOS for my OS HD and after some difficulty booting I was able to mount the external drive.

[IMG]http://imageshack.us/photo/my-images/850/goodiedrivework.png/[/IMG]
[IMG]http://imageshack.us/photo/my-images/850/goodiedrivework.png/][IMG=http://img850.imageshack.us/img850/1833/goodiedrivework.png[/IMG][IMG]http://imageshack.us/photo/my-images/850/goodiedrivework.png/%5D%5BIMG=http://img850.imageshack.us/img850/1833/goodiedrivework.png%5D%5B/IMG%5D%5B/URL%5D[/IMG]
[IMG]http://ubuntuforums.org/%5BURL=http://imageshack.us/photo/my-images/850/goodiedrivework.png/%5D%5BIMG%5Dhttp://img850.imageshack.us/img850/1833/goodiedrivework.png%5B/IMG%5D%5B/URL%5D[/IMG]
[IMG]http://imageshack.us/photo/my-images/850/goodiedrivework.png/[/IMG]

[IMG]http://imageshack.us/photo/my-images/850/goodiedrivework.png/[/IMG]

---

