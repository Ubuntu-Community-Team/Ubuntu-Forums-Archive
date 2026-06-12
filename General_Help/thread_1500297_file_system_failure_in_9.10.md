---
title: "file system failure in 9.10"
date: 2010-06-03
forum: General Help
---

### Post by grumpy.biatch on 2010-06-03
I get following error while mounting 9.10 partition (it wont boot so i installed 10.04 on extended partition. 


:~$ dmesg | tail
[  211.736094] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  211.736497] EXT3-fs: group descriptors corrupted!
[  576.502761] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  576.503143] EXT3-fs: group descriptors corrupted!
[  807.901678] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  807.902080] EXT3-fs: group descriptors corrupted!
[ 1230.978223] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 1230.979167] EXT3-fs: group descriptors corrupted!
[ 1552.788041] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 1552.788466] EXT3-fs: group descriptors corrupted!

---

### Post by grumpy.biatch on 2010-06-04
> **grumpy.biatch said:**
> I get following error while mounting 9.10 partition (it wont boot so i installed 10.04 on extended partition. 


:~$ dmesg | tail
[  211.736094] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  211.736497] EXT3-fs: group descriptors corrupted!
[  576.502761] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  576.503143] EXT3-fs: group descriptors corrupted!
[  807.901678] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  807.902080] EXT3-fs: group descriptors corrupted!
[ 1230.978223] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 1230.979167] EXT3-fs: group descriptors corrupted!
[ 1552.788041] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 1552.788466] EXT3-fs: group descriptors corrupted!

Managed to recover some data but it was hectic -

Here is what I did -

xxxxxx@xxxxxx-desktop:~$ sudo fdisk -l
[sudo] password for xxxxxx: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe695e695

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       34121   274068900   83  Linux
/dev/sda2           34121       38913    38499169+   5  Extended
/dev/sda5           38735       38913     1437817+  82  Linux swap / Solaris
/dev/sda6           34121       38076    31769600   83  Linux
/dev/sda7           38076       38734     5290727   82  Linux swap / Solaris

Partition table entries are not in disk order

xxxxxx@xxxxxx-desktop:~$ sudo  mke2fs -n /dev/sda1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
17129472 inodes, 68517225 blocks
3425861 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2091 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

root@xxxxxx-desktop:~# dumpe2fs /dev/sda1|grep -i superblock
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: A block group is missing an inode table while reading journal inode

**Fix: sudo fsck /dev/device (sda1,2,3,etc.or hda1,2,3, etc.)**

It takes a lot of time depending upon data size. Had to fix a pencil on y key in order to sort out 17 MN inode and took 2 days. 
UPS doesnt make a good power supply and users should be careful when mains are down. Switch of the machine, unmount all devices. 

The fix came from Fedora User. 

P.S. - 9.10 users must back up their data and migrate to 10.04 with an independent data partition. :)

Hitting it at wife - Life is short, data is important; shoes can wait!

---

### Post by dino99 on 2010-06-04
why is there 2 swap partitions ? Have you a /home to store your data ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by grumpy.biatch on 2010-06-04
> **dino99 said:**
> why is there 2 swap partitions ? Have you a /home to store your data ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

I resized 9.10 using gparted and installed 10.04 in order to rescue the data. Thus managed to boot in unresponsive machine and check the system. I wanted to rescue 9.10 and get to the boot so kept the 9.10 swap intact but that was beyond any repairs.

---

### Post by grumpy.biatch on 2010-06-04
> **dino99 said:**
> why is there 2 swap partitions ? Have you a /home to store your data ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

Gparted works well in case of system rescue. In addition systemrescuecd has more tools. If you so choose to download and waste a CD use systemrescuecd.

---

### Post by dino99 on 2010-06-04
so mark the thread "solved" if it is

---

### Post by grumpy.biatch on 2010-06-04
> **dino99 said:**
> so mark the thread "solved" if it is

Trying to figure that out for last 30 mins.

---

### Post by cbecker78 on 2010-06-04
> **grumpy.biatch said:**
> Trying to figure that out for last 30 mins.

click on the "thread tools" above.  "mark as solved" is in there.

---

### Post by grumpy.biatch on 2010-06-04
> **cbecker78 said:**
> click on the "thread tools" above.  "mark as solved" is in there.

Thanks.

---

