---
title: "ca'nt creat partition in iomega disk"
date: 2011-09-26
forum: General Help
---

### Post by JCM_Pico on 2011-09-26
Helllo

I've a iomega external hard disk. from factory it comes with a NTFS partition and a small partition with something from iomega (which I don't want).

Since I only use the drive in linux, I opened the disk utility and formatted the entire disk, has a master boot record...
When I was trying to create a partition an error occurred:

```
 Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdb, start=0, size=749422370816, type=0x83
Entering MS-DOS parser (offset=0, size=749422370816)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
Warning: Device /dev/sdb has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

```

Since the iomega stuff wasn't deleted it is now giving me problems, because I can't create a partition.

Does anyone know how to workaround this?

the iomega stuff is has a virtual cd

---

### Post by ajgreeny on 2011-09-26
Try using gparted on the live CD/USB.

Open up the iomega disk in gparted and go to **Device ->Create partition table**.  That will warn you that everything on the disk will be lost, but as that doesn't matter to you, accept it and go ahead making an ms-dos partition table (the default for gparted).

You should now have an unallocated disk and can then make a new partition or partitions on it in whatever format type you want.

---

### Post by e79 on 2011-09-26
I recently bought 2 x Iomega eGo 1Tera for a customer who wanted it for simple backups rotations. I ran into several issues because of the encryption and the VirtualCD partition.

After calling Iomega support, they gave me some links to :

1. Remove the encryption from the USB 3.0 drive:
[https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24752/kw/encryption](https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24752/kw/encryption)

2. Remove the CD Partition on the drive:
[https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24749/kw/encryption/related/1](https://iomega-na-en.custhelp.com/app/answers/detail/a_id/24749/kw/encryption/related/1)

I was then able to do whatever I wanted with the drive.

Hope this helps

---

### Post by JCM_Pico on 2011-09-26
1 - ajgreeny it was a nice idea, I was able to format the drive and create a ext4 partition, but when I mount the drive in any computer I'm not able to write. --> read only file system

2 - a79 great advice,  I had already stumble on that FAQ, and it solved one of my problems with the drive. --> There's no more iomeg virtual cd on it

Now, I got the drive clean, but I'm not being able to format the entire partition to ext4. With disk utility it keeps formating forever and it never ends, with gparted I get a read only filesystem...](*,)

---

### Post by ajgreeny on 2011-09-26
The permissions will all be wrong for the ext4 partition and for ease I suggest you both make and then label the ext4 partition using gparted.   Call it **iomega**.

Now you need to change the ownership of the disk/partition to you so attach it so it mounts then use . ```
sudo chown -R *username:username* /media/iomega
``` And set read write and excecute permissions for anybody ```
sudo chmod -R 777 /media/iomega
``` This will allow full access to any directories and subdirectories on the disk for anyone and should work on any Linux machine.

Make sure you get the mountpoint right or you could cause big trouble, and sustitute your own username where I have used *username*.

---

### Post by srs5694 on 2011-09-26
What version of Ubuntu are you using? I recall a thread recently in which a person found that the support for disks with 4096-byte sectors was messed up in a slightly older version of Ubuntu (maybe 10.04, but I don't recall correctly). Upgrading to a more recent kernel, or maybe a whole Ubuntu upgrade, fixed the problem. You could test this out by using a "live CD" for a more recent version if you're running an older one.

---

### Post by e79 on 2011-09-26
That's a good suggestion ajgreeny gave you. I would add, have a look here:

[https://bbs.archlinux.org/viewtopic.php?id=114025](https://bbs.archlinux.org/viewtopic.php?id=114025)

Maybe manual formatting and mounting would help you....

---

### Post by JCM_Pico on 2011-09-27
Problem solved...

I was able to recover the HD with iomega software in widowz, next I got back to ubuntu and formated that partition using the disk utility...

Now I got the HD without the Iomeg virtual cd and ext4 formated :D

Thank you all

---

