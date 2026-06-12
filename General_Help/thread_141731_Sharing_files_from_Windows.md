---
title: "Sharing files from Windows"
date: 2006-03-08
forum: General Help
---

### Post by cabber on 2006-03-08
I currently have XP installed on its own drive and Ubuntu on its own drive.  Ubuntu is installed on a 400G drive.  I partitioned the drive with 10gigs for the install.  That leave 390G for sharing and what not.  I'd like to get some advise on how to partition the remaining space of the drive.   Keep in mind I would like to be able to view files between Ubuntu and XP (if that is possible) and vice versa (if that possible). 

I used partition magic to create a 50G FAT32 partition and cannot find it.  It does not show up on my Ubuntu desktop.  Maybe it is here, but I have no idea how to find it.  Thanks.

---

### Post by andrewsawyer on 2006-03-08
Have a look in System >> Administration >> Disks.  You should be able to find and mount the partition from there.

---

### Post by akiro.yamamoto on 2006-03-08
These are the typical enties (taken from my /etc/fstab file)
```

/dev/hdd2       /media/data     vfat    user,umask=000        0       0
/dev/hdd1       /media/extra    ntfs    user,ro,umask=0222        0       0
/dev/hdb1       /media/old-home ext3    defaults        0       2

```
Of course if your mount points and /dev entries will be different to what I have here
If you are unable to figure out what your /dev entries are you can use Gparted to
list all the partitions on your hard disks as well as their file types. That should give
you a goo start point. You may also have to create the mount point (directory) 
where your partition will be mounted 
```

sudo mkdir /media/data (This will create the /data dir used as a mount point)

```
Personally I would use ext3 as my file system to exchange info between XP & Linux
I would format my partition as ext3 and then install the ext2 fs driver in windows.
Hope this helps to get you on your way ;)

---

