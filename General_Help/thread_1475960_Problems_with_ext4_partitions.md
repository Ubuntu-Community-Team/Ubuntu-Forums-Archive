---
title: "Problems with ext4 partitions"
date: 2010-05-07
forum: General Help
---

### Post by flight243 on 2010-05-07
Hi!

First of all thank you for reading this. I'm sorry for the huge post but I think it'd be better to illustrate the whole procedure I'm taking, and definitely need some help. I'm pretty frustrated now.

Well, since yesterday I'm having issues with a hard disk and I can't find a solution. The hdd is in a external enclosure connected to my computer via usb. When I plug the cable, dmesg shows a lot of errors


```

scsi 6:0:0:0: Direct-Access     Maxtor 6 E040L0           0811 PQ: 0 ANSI: 0
sd 6:0:0:0: Attached scsi generic sg1 type 0
usb-storage: device scan complete
sd 6:0:0:0: [sdc] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
sd 6:0:0:0: [sdc] Test WP failed, assume Write Enabled
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sd 6:0:0:0: [sdc] Test WP failed, assume Write Enabled
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sdc: sdc1 sdc2 < sdc5 >
sd 6:0:0:0: [sdc] Test WP failed, assume Write Enabled
sd 6:0:0:0: [sdc] Assuming drive cache: write through
sd 6:0:0:0: [sdc] Attached SCSI disk
usb 1-1: USB disconnect, address 2
sd 6:0:0:0: [sdc] Unhandled error code
sd 6:0:0:0: [sdc] Result: hostbyte=0x07 driverbyte=0x00
sd 6:0:0:0: [sdc] CDB: cdb[0]=0x28: 28 00 00 1f de 41 00 00 40 00
end_request: I/O error, dev sdc, sector 2088513
Buffer I/O error on device sdc5, logical block 0
Buffer I/O error on device sdc5, logical block 1
Buffer I/O error on device sdc5, logical block 2
Buffer I/O error on device sdc5, logical block 3
Buffer I/O error on device sdc5, logical block 4
Buffer I/O error on device sdc5, logical block 5
Buffer I/O error on device sdc5, logical block 6
Buffer I/O error on device sdc5, logical block 7
sd 6:0:0:0: [sdc] Unhandled error code
sd 6:0:0:0: [sdc] Result: hostbyte=0x01 driverbyte=0x00
sd 6:0:0:0: [sdc] CDB: cdb[0]=0x28: 28 00 00 1f de 81 00 00 40 00
end_request: I/O error, dev sdc, sector 2088577
Buffer I/O error on device sdc5, logical block 8
Buffer I/O error on device sdc5, logical block 9
sd 6:0:0:0: [sdc] Unhandled error code
sd 6:0:0:0: [sdc] Result: hostbyte=0x01 driverbyte=0x00
sd 6:0:0:0: [sdc] CDB: cdb[0]=0x28: 28 00 00 1f de c1 00 00 40 00
end_request: I/O error, dev sdc, sector 2088641

```

and so on...
The disk has 2 partitions: a swap and an **ext4** contained in an extended partition with all my Ubuntu system. When I run fdisk I get the following:

```

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b1c6b1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         130     1044193+  82  Linux swap / Solaris
/dev/sdc2             131        4865    38033887+   5  Extended
/dev/sdc5             131        4865    38033856   83  Linux


```

I've tried to run a e2fsck on the disk but I get a superblock error. I've searched along the internet and I've found some people with similar issues suggesting the use of testdisk. And so did I... first of all looking for superblocks

```

Ext2 superblock found at sector 32768000 (block=4096000, blocksize=4096)
  Linux                  130   1  1  4864 254 63   76067712
superblock 32768, blocksize=4096 []
superblock 98304, blocksize=4096 []
superblock 163840, blocksize=4096 []
superblock 229376, blocksize=4096 []
superblock 294912, blocksize=4096 []
superblock 819200, blocksize=4096 []
superblock 884736, blocksize=4096 []
superblock 1605632, blocksize=4096 []
superblock 2654208, blocksize=4096 []
superblock 4096000, blocksize=4096 []

```

and later trying to run again e2fsck with the param -b. Unsucessfuly

I've also tried to analyse the hdd with this tool:

```

Current partition structure:
 1 * Linux Swap               0   1  1   129 254 63    2088387
 2 E extended               130   0  1  4864 254 63   76067775
No EXT2, JFS, Reiser, cramfs or XFS marker
 5 L Linux                  130   1  1  4864 254 63   76067712
 5 L Linux                  130   1  1  4864 254 63   76067712

```and got this ugly message

```

This partition ends after the disk limits. (start=2361681, size=76067712, end=78429392, disk end=78165360)
Disk /dev/sdc - 40 GB / 37 GiB - CHS 4865 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (40 GB / 37 GiB) seems too small! (< 40 GB / 37 GiB)
The following partition can't be recovered:
     Linux                  147   2  1  4882   0 63   76067712
     EXT3 Large file Sparse superblock Recover, 38 GB / 36 GiB

```I also run GParted and this is what I got:

[IMG]http://i41.tinypic.com/ictvh1.png[/IMG]


Note the partition on /dev/sdc5 marked as **ext3** instead of **ext4** which is the format it actually has.

I have no more ideas to get my hard disk and my data back. Next thing I'm trying is to create an image of the disk and run photorec but I guess that won't be unsuccessful either. 

Have you experienced similar issues? What should I do now? Can somebody help me?

Thanks in advance,

Alex

---

