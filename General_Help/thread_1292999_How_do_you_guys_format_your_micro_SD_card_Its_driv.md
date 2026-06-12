---
title: "How do you guys format your micro SD card? Its driving me nuts."
date: 2009-10-16
forum: General Help
---

### Post by amitabhishek on 2009-10-16
I have a 4GB micro SD card (SDHC) which I want to partition  between ext2 & FAT16 filesystems. I have tried both Gparted and fdisk. No success whatsoever. The result of my fdisk command is pasted below:

> Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-15310, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-15310, default 15310): +256M

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (8194-15310, default 8194): 
Using default value 8194
Last cylinder, +cylinders or +size{K,M,G} (8194-15310, default 15310): +200M

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

I have attached screenshot of Gparted. I don't know if this is a kernel bug? Is there any other application in repo which I can use for partitioning? Any help will be greatly appreciated.:(

---

### Post by beastrace91 on 2009-10-16
What version of Ubuntu are you using? If it is indeed a kernel issue perhaps you can try booting into a different kernel from grub? Or even booting from a LiveCD of another Ubuntu version (meaning whole different kernel) and see if that helps.

~Jeff

---

### Post by amitabhishek on 2009-10-16
> **beastrace91 said:**
> What version of Ubuntu are you using? If it is indeed a kernel issue perhaps you can try booting into a different kernel from grub? Or even booting from a LiveCD of another Ubuntu version (meaning whole different kernel) and see if that helps.

~Jeff

Its Jaunty...same issue in other distros too...any other Linux tool other than fdisk/gparted? Am I missing anything? BTW keep (any) one partition table on the card is working!!!:confused:

---

### Post by Giblet5 on 2009-10-16
Did you try pulling the card out and reinserting it after you partitioned it?

I always use fdisk because it has never failed to work. If fdisk doesn't work, something else is wrong. That simple.

Once you have partitioned the drive, you have to format it. Remember that FAT16 can be no larger than 32MB...

Here's my terminal session, partitioning an 8G stick and formatting it: ```
giblet5@meatbag$ sudo fdisk /dev/sdh

Command (m for help): p

Disk /dev/sdh: 8254 MB, 8254390272 bytes
254 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15748 * 512 = 8062976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        1023     8055071    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 253, 62) logical=(1022, 253, 62)

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1023, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1023, default 1023): +32M

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 6
Changed system type of partition 1 to 6 (FAT16)

Command (m for help): p

Disk /dev/sdh: 8254 MB, 8254390272 bytes
254 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15748 * 512 = 8062976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1           5       39339    6  FAT16

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (6-1023, default 6): 
Using default value 6
Last cylinder, +cylinders or +size{K,M,G} (6-1023, default 1023): 
Using default value 1023

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 83

Command (m for help): p

Disk /dev/sdh: 8254 MB, 8254390272 bytes
254 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15748 * 512 = 8062976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1           5       39339    6  FAT16
/dev/sdh2               6        1023     8015732   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
giblet5@meatbag$ 
```

(Stick was mounted previously, so I pull the stick, wait 5 seconds, plug it back in)


```
giblet5@meatbag$ sudo mkfs.msdos /dev/sdh1
mkfs.msdos 3.0.3 (18 May 2009)
mkfs.msdos: /dev/sdh1 contains a mounted file system.
giblet5@meatbag$ sudo umount /dev/sdh1
giblet5@meatbag$ sudo mkfs.msdos /dev/sdh1
mkfs.msdos 3.0.3 (18 May 2009)
giblet5@meatbag$ sudo mkfs.ext3 /dev/sdh2
mke2fs 1.41.9 (22-Aug-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
501952 inodes, 2003933 blocks
100196 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2055208960
62 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:
```

---

### Post by amitabhishek on 2009-10-16
Thanks! It did partition but now formatting seems to be a problem.

>  Device               Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1p1               1       32769     1048600    b  W95 FAT32
/dev/mmcblk0p1p2           32770      124160     2924512   83  Linux

Command (m for help): ^C
amit@amit-laptop:~$ sudo mkfs.ext3 /dev/mmcblk0p1p2
mke2fs 1.41.4 (27-Jan-2009)
Could not stat /dev/mmcblk0p1p2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
amit@amit-laptop:~$ 


Any ideas?

BTW I did "w" before ^C; this is just to give you an idea of the partition table created ;).

---

### Post by Giblet5 on 2009-10-16
> **amitabhishek said:**
> Thanks! It did partition but now formatting seems to be a problem.

Any ideas?

BTW I did "w" before ^C; this is just to give you an idea of the partition table created ;).

Your drive name is ... unlikely.

What is the output of ```
sudo fdisk -l
```

(look for the 4G card...)

---

### Post by amitabhishek on 2009-10-16
> **Giblet5 said:**
> Your drive name is ... unlikely.

What is the output of ```
sudo fdisk -l
```

(look for the 4G card...)

While inside fdisk...this is the output...

```
Command (m for help): p

Disk /dev/mmcblk0p1: 4068 MB, 4068474880 bytes
4 heads, 16 sectors/track, 124160 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0xc6063b13

          Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1p1               1       32769     1048600    b  W95 FAT32
/dev/mmcblk0p1p2           32770      124160     2924512   83  Linux

```

However...

```
amit@amit-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac13f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12163    97699266   83  Linux
/dev/sda2           12164       19457    58589055    5  Extended
/dev/sda5           12164       19214    56637126    b  W95 FAT32
/dev/sda6           19215       19457     1951866   82  Linux swap / Solaris

Disk /dev/mmcblk0: 4072 MB, 4072669184 bytes
53 heads, 52 sectors/track, 2886 cylinders
Units = cylinders of 2756 * 512 = 1411072 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               3        2887     3973120    b  W95 FAT32
amit@amit-laptop:~$ 

```

Gparted output is also attached (just in case)

---

### Post by Giblet5 on 2009-10-16
Try this:

#1 unmount the fat fs: ```
sudo unmount /dev/mmcblk0p1
```

#2 partition the disk: ```
sudo fdisk /dev/mmcblk0
Command (m for help): **d**
Partition number (1-4): **2**

Command (m for help): **d**
Selected partition 1

Command (m for help): **n**
Command action
   e   extended
   p   primary partition (1-4)
**p**
Partition number (1-4): **1**
First cylinder (1-1023, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-1023, default 1023): **+2000M**

Command (m for help): **t**
Selected partition 1
Hex code (type L to list codes): **b**
Changed system type of partition 1 to b (W95 FAT32)

Command (m for help): **n**
Command action
   e   extended
   p   primary partition (1-4)
**p**
Partition number (1-4): **2**
First cylinder (262-1023, default 262): 
Using default value 262
Last cylinder, +cylinders or +size{K,M,G} (262-1023, default 1023): **Hit Enter**
Using default value 1023

Command (m for help): **t**
Partition number (1-4): **2**
Hex code (type L to list codes): **83**

Command (m for help): **w**
The partition table has been altered!

Calling ioctl() to re-read partition table.
```

#3 pull the SD card out, count to five, plug it back in (this does the same thing that rebooting does).

#4 Wait for it.... waaaaait for it... now, unmount the fat fs again: 
################## THIS IS ALL YOU NEED TO FORMAT THE FAT PARTITION ##############
```
sudo unmount /dev/mmcblk0p1
```

#5 format the fat filesystem ```
sudo mkfs.vfat /dev/mmcblk0p1
```
##################################################################################

#6 format the ext3 fs: ```
sudo mkfs.ext3 /dev/mmcblk0.p2
```

#7 pull the SD card out, count to five, plug it in.

All good?

---

### Post by amitabhishek on 2009-10-16
Sounds funny and little unbelievable...but now the drive is not reading any of my uSD cards (incl. a 512MB one.). Don't know what problem has crept in???? Will keep u updated on this thread while I try to find out the cause.

Thanks anyway..will bug you shortly ;)

---

### Post by ackley on 2009-10-16
I had this happen to me on my wife's laptop the other day when I was trying to format my 8 gig sdhc card while my laptop was down. I restarted her computer & everything worked fine after that. Not sure why, but it did.

---

### Post by amitabhishek on 2009-10-16
SDHC card from my phone is working fine. But these 4GB and 512MB ones are just not getting mounted; even after restarts (as such my plate was full:mad:)

---

### Post by Giblet5 on 2009-10-16
> **amitabhishek said:**
> SDHC card from my phone is working fine. But these 4GB and 512MB ones are just not getting mounted; even after restarts (as such my plate was full:mad:)

It's worth remombering that linux won't auto-mount the drive if it doesn't see a formatted filesystem.

```
sudo fdisk -l
``` will tell you what devices are plugged in, even if they have no partitions at all.

---

### Post by amitabhishek on 2009-10-17
Yay!!!! That worked....thanks a tonne!


```
Device Boot         Start         End      Blocks   Id  System
/dev/mmcblk0p1               1       32769     1048600    b  W95 FAT32
/dev/mmcblk0p2           32770      124288     2928608   83  Linux

``` :)

---

### Post by Satoyaki on 2012-04-01
didnt work for me:

fdisk: invalid option -- '1'

cant get permisson, tried sudo wont work

---

### Post by gordintoronto on 2012-04-02
It's the letter "l" not the digit "1".

---

