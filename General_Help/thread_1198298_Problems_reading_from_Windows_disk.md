---
title: "Problems reading from Windows disk"
date: 2009-06-27
forum: General Help
---

### Post by kokkus on 2009-06-27
Hey.
After I installed Ubuntu 9.04 the system can sometimes not read the windows partition and the files on that disk.
So is there a way to mount all the disks to be readed durring the booting process and not after I have logged in?

---

### Post by colau on 2009-06-27
> **kokkus said:**
> Hey.
After I installed Ubuntu 9.04 the system can sometimes not read the windows partition and the files on that disk.
So is there a way to mount all the disks to be readed durring the booting process and not after I have logged in?
Can you post 
```

sudo cat /etc/fstab

```

---

### Post by jocko on 2009-06-27
> **colau said:**
> Can you post 
```

sudo cat /etc/fstab

```
You don't need sudo to** read **fstab, only to write to it. Don't tell people to use sudo when it's not needed.

@op: Post the output of:```
cat /etc/fstab
```And:```
ls -la /dev/disk/by-uuid/
```And:```
sudo fdisk -l
```

---

### Post by kokkus on 2009-06-27
Sure. But it couldn't find the disk-uuid thing.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=1f172296-8736-413a-bf43-2ec71506c25b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c82db6c4-dc00-4126-9bd7-58c766d83df6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1 /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0
/dev/sda1 /media/ntfs ntfs-3g defaults,locale=en_US.utf8 0 0



Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44d344d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d595ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29293   235295991   83  Linux
/dev/sdb2           29294       30515     9815715    5  Extended
/dev/sdb5           29294       30515     9815683+  82  Linux swap / Solaris

---

### Post by colau on 2009-06-27
Unmount your all drives then post 
```

sudo cat /etc/fstab

```

---

### Post by jocko on 2009-06-27
> **kokkus said:**
> Sure. But it couldn't find the disk-uuid thing
Are you sure? Try again. Just paste the command into a terminal. It has to be there, otherwise you would not even be able to boot...
Without that output, there is no easy way for us to tell you how to add the proper entry to fstab...

---

### Post by jocko on 2009-06-27
> **colau said:**
> Unmount your all drives then post 
```

sudo cat /etc/fstab

```
Again, don't tell anyone to use sudo with a command that can be run as a normal user, and as you can see, he has already posted his fstab. And why would he need to unmount anything to show the contents of fstab???

---

### Post by colau on 2009-06-27
> **kokkus said:**
> Sure. But it couldn't find the disk-uuid thing.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=1f172296-8736-413a-bf43-2ec71506c25b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c82db6c4-dc00-4126-9bd7-58c766d83df6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1 /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0
/dev/sda1 /media/ntfs ntfs-3g defaults,locale=en_US.utf8 0 0



Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44d344d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d595ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29293   235295991   83  Linux
/dev/sdb2           29294       30515     9815715    5  Extended
/dev/sdb5           29294       30515     9815683+  82  Linux swap / Solaris

```

sudo mkdir /media/DRIVE1
sudo mkdir /media/DRIVE2

```

Remove these two lines from /etc/fstab
```

/dev/sdc1 /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0
/dev/sda1 /media/ntfs ntfs-3g defaults,locale=en_US.utf8 0 0

```

Add these lines in your /etc/fstab .
```

/dev/sdc1 /media/DRIVE1 vfat defaults  0 0
/dev/sda1 /media/DRIVE2 ntfs-3g defaults  0 0

```
Restart your system .
Does this work ?

---

### Post by colau on 2009-06-27
To mount ntfs drive during boot time see post no 10 from [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=1168719&highlight=mount+ntfs")

---

