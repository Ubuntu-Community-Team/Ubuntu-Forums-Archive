---
title: "Missing superblock?"
date: 2012-01-04
forum: General Help
---

### Post by kylegio on 2012-01-04
Ok! so i haven't touched the partitions on this drive, however it seems they have become messed up. The drive still APPEARS to work fine, however I am booting multiple operating systems and all other OS's have lost the ability to read from the drive in question.

Ubuntu still reads the drive just fine, but some oddities appear when I try to inspect the partitions.

First: in ubuntu's build in disk utility it shows the partition as being a 2TB ext4 partition, but it also says "Partitioning: Not Partitioned"   checking the filesystem comes back as clean. 

Second: In gparted it has an asterisk by the partition, when i pull up the "information" it says "couldn't find valid superblock" & "no such file or directory while trying to open /dev/sda1"

While doing some more investigating, sure enough /dev/sda1 doesn't exist, the partition in the disk utility says /dev/sda (no partition number)... this seems odd to me

I have attached a screenshot so that you could see.

the following is some terminal output that might be helpful.
```
**USER**@**COMPUTERNAME**:~$ sudo mke2fs -n /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488378646 blocks
24418932 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

**USER**@**COMPUTERNAME**:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.41.14 (22-Dec-2010)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
**USER**@**COMPUTERNAME**:~$ sudo dumpe2fs /dev/sda | grep -i superblock
dumpe2fs 1.41.14 (22-Dec-2010)
  Primary superblock at 0, Group descriptors at 1-117
  Backup superblock at 32768, Group descriptors at 32769-32885
  Backup superblock at 98304, Group descriptors at 98305-98421
  Backup superblock at 163840, Group descriptors at 163841-163957
  Backup superblock at 229376, Group descriptors at 229377-229493
  Backup superblock at 294912, Group descriptors at 294913-295029
  Backup superblock at 819200, Group descriptors at 819201-819317
  Backup superblock at 884736, Group descriptors at 884737-884853
  Backup superblock at 1605632, Group descriptors at 1605633-1605749
  Backup superblock at 2654208, Group descriptors at 2654209-2654325
  Backup superblock at 4096000, Group descriptors at 4096001-4096117
  Backup superblock at 7962624, Group descriptors at 7962625-7962741
  Backup superblock at 11239424, Group descriptors at 11239425-11239541
  Backup superblock at 20480000, Group descriptors at 20480001-20480117
  Backup superblock at 23887872, Group descriptors at 23887873-23887989
  Backup superblock at 71663616, Group descriptors at 71663617-71663733
  Backup superblock at 78675968, Group descriptors at 78675969-78676085
  Backup superblock at 102400000, Group descriptors at 102400001-102400117
  Backup superblock at 214990848, Group descriptors at 214990849-214990965
**USER**@**COMPUTERNAME**:~$ sudo dumpe2fs /dev/sda1 | grep -i superblock
dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: No such file or directory while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
**USER**@**COMPUTERNAME**:~$ 

```



What i am looking for is a way of correcting the issue, without data loss. Oddly enough it does work right now, so worst case scenario is i have to go buy another 2tb drive, copy everything off... but i would like to avoid that

---

