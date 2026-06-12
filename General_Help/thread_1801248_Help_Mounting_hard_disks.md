---
title: "Help Mounting hard disks"
date: 2011-07-10
forum: General Help
---

### Post by miza on 2011-07-10
Hi, i am using Ubuntu ver. 11.04 installed on a 16gb usb. It was running ok until it could not mount any hard disk. Both hard disks are ntfs formated. one hard disk is normally connected throw the ide or sata and the other one is western digital external hard disk. when i try to mount any of the two hard disks i get this message: 

"Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command."

 i searched for solutions but didn't find anything to solve my problem. I found that these info are required.

The output for sudo sfdisk -l is :
"Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  60798   60799- 488366943+   7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 16177 cylinders, 64 heads, 32 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/2/63 (instead of 16177/64/32).
For this listing I'll assume that geometry.
Units = cylinders of 64512 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+ 262948- 262949-  16565728+   c  W95 FAT32 (LBA)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

Disk /dev/sdc: 121597 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdc1          0+ 121597- 121598- 976728064    7  HPFS/NTFS
/dev/sdc2          0       -       0          0    0  Empty
/dev/sdc3          0       -       0          0    0  Empty
/dev/sdc4          0       -       0          0    0  Empty"

the output for sudo blkid:
"/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="055540bb-55ac-5547-b2be-c02a54b42235" TYPE="ext2" 
/dev/sda1: UUID="840C1D980C1D8678" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="13ED-235C" TYPE="vfat" 
/dev/sdc1: LABEL="My Passport" UUID="8A2CF4F62CF4DE5F" TYPE="ntfs" "

The content of "/etc/fstab" is :
"aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0"

please help me as i need to edit files from the hard for work.

---

