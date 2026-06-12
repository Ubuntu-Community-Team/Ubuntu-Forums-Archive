---
title: "unable to mount .img file"
date: 2010-11-16
forum: General Help
---

### Post by squeak24 on 2010-11-16
I have created a .mg file using DD of a failed hard drive. I have tried usng scalpel and foremost to extract the data, scalpel crashed the computer, and foremost isn't happy as I have files over 2GB. foremost did extract some of the files. Since then I have tried to mount the .img file so I can extract the data that way, but it just isn't working.

The original Hard Drive was formatted as FAT32, in terminal I have inputted

sudo mount -t vfat -o loop /media/Elements/passport2.img /mnt/temp

but it comes up with the following error

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any ideas what I am doing wrong? I have searched, other people seem to have the same issues, but there is nothing to explain how this has been fixed.

Many thanks in advance.

---

### Post by mirearts KING SUNNY on 2010-11-16
If its a Windows failed drive, then you need windows to securely remove the drive before it can be mounted on Ubuntu. Attach your drive to a windows OS and shutdown the PC. If you have deleted the damaged drive partition, then dont worry... Download the application File Inspector Recovery and run it on windows.

---

### Post by Van Fanel on 2010-11-18
I have a somewhat similar problem:

My hard drive just died on me, but before its death I was able to create an image of the \home partition where my important files are.
Now I wanted to mount this image, but I keep getting the same error message as mentioned above:
```

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

Any ideas how I can mount this image properly? I tried searching Google, but what I've found so far didn't help.

I am also trying to use foremost and scalpel to recover my files from this image. So far I successfully extracted some files, but there are still many that I would like to get my hands on. For example, I have Matlab and Python scripts as well as some binary files that I need to recover. I've been trying some trial and error attempts to recover these files, but so far to no avail.
Does someone have any intel on how to use the config file of scalpel in order to search for these specific file types?

---

### Post by psusi on 2010-11-18
Try as it suggests and look at the output of dmesg | tail.

Also are you sure it is fat32 and not ntfs?

---

### Post by gmargo on 2010-11-18
You can mount using an offset into the image file.  Details in this thread: [http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

---

### Post by linux18 on 2010-11-18
just try ```
 sudo mount -o loop /path/to/.img /mount/location 
```

---

### Post by squeak24 on 2010-11-19
> **linux18 said:**
> just try ```
 sudo mount -o loop /path/to/.img /mount/location 
```

I Tried that and it comes up with

```

sudo mount -o loop /media/Elements/passport.img /mnt/temp
mount: you must specify the filesystem type

```

The origional hard drive was FAT32, I have this on a new external hard drive that is NTFS, this is where the image is stored.

> **gmargo said:**
> You can mount using an offset into the image file.  Details in this thread: [http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

I have tried what is in this thread, it comes up with the following:

```

@bob-ubuntu:~$ fdisk /media/Elements/passport.img
You must set cylinders.
You can do this from the extra functions menu.

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): 
```

---

### Post by gmargo on 2010-11-19
You missed the "-l" option on fdisk.  Or you could type a "p" at the command prompt.

---

### Post by squeak24 on 2010-11-19
> **gmargo said:**
> You missed the "-l" option on fdisk.  Or you could type a "p" at the command prompt.

When I try that I get

```

partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help):   


```

I have no idea what is going wrong here, any help is greatly appreciated.

When I try what fdisk suggests it comes up with the following


```

Command (m for help): c
DOS Compatibility flag is not set

Command (m for help): u
Changing display/entry units to sectors
```

---

### Post by psusi on 2010-11-19
> **gmargo said:**
> You missed the "-l" option on fdisk.  Or you could type a "p" at the command prompt.

Read this again.

---

### Post by linux18 on 2010-11-20
if you have the disk space, just dd the img to some free space on the drive, it shouls then act like a partition and you'll be able to extract the data

---

### Post by squeak24 on 2010-11-21
> **psusi said:**
> Read this again.

sorry I thought I ad copied that bit, looks like I hadn't, this is what it comes with

> 
fdisk -l /media/Elements/passport.img
You must set cylinders.
You can do this from the extra functions menu.

Disk /media/Elements/passport.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b1f0c5a

                       Device Boot      Start         End      Blocks   Id  System



[quote=linux18]
if you have the disk space, just dd the img to some free space on the  drive, it shouls then act like a partition and you'll be able to extract  the data 	
[/quote]

I don't have enough room on my internal hard drive to do that.

I am contemplating getting a Mac next week which will have enough space, will have to take a look

---

### Post by psusi on 2010-11-21
Try -lu

---

### Post by squeak24 on 2010-11-22
> **psusi said:**
> Try -lu

Thanks for your help there, but that came up with

> 
@bob-ubuntu:~$ fdisk -lu /media/Elements/passport.img
You must set cylinders.
You can do this from the extra functions menu.

Disk /media/Elements/passport.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b1f0c5a

                       Device Boot      Start         End      Blocks   Id  System


---

### Post by gmargo on 2010-11-22
> **squeak24 said:**
> 
Device Boot      Start         End      Blocks   Id  System                      

So this says to me that you have no valid partition table in that disk image (unless your omitting something?).  Exactly how did you create the disk image?  Was it of a whole disk or of just a partition on the disk?

Try using "sfdisk -l filename" - sfdisk will also complain but might give more info.

---

### Post by squeak24 on 2010-11-23
> **gmargo said:**
> So this says to me that you have no valid partition table in that disk image (unless your omitting something?).  Exactly how did you create the disk image?  Was it of a whole disk or of just a partition on the disk?

Try using "sfdisk -l filename" - sfdisk will also complain but might give more info.

Will give that a go later, I used the command

sudo dd if-/dev/sdb of=/media/Elements/passport.img

I have extracted some of the files using foremost, but as there is one file that is over 2GB this wasn't happy and got stuck when it got to that file. I also tried using Scalpel, but after two days of processing my computer crashed.

that came up with

```

sudo sfdisk -l /media/Elements/passport.img
[sudo] password for gary: 
Disk /media/Elements/passport.img: cannot get geometry

Disk /media/Elements/passport.img: 13955 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/media/Elements/passport.img1          0       -       0          0    0  Empty
/media/Elements/passport.img2          0       -       0          0    0  Empty
/media/Elements/passport.img3          0       -       0          0    0  Empty
/media/Elements/passport.img4          0       -       0          0    0  Empty
```

With the -lu it came up with

```
sudo sfdisk -lu /media/Elements/passport.img
unrecognized format - using sectors

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 125564039  125563977   7  HPFS/NTFS
/dev/sda2     125564040 156296384   30732345   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     125564103 154914794   29350692  83  Linux
/dev/sda6     154914858 156296384    1381527  82  Linux swap / Solaris

Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048 976769023  976766976   7  HPFS/NTFS
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
```

I have just tried to fdisk and mount the failed Hard Drive. This is what comes up:

```
sudo sfdisk -l /dev/sdc

Disk /dev/sdc: 19457 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type
No partitions found
```

```
sudo fdisk -l /dev/sdc

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a000000

Disk /dev/sdc doesn't contain a valid partition table
```

```
sudo mount -o loop -t vfat /dev/sdc /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

