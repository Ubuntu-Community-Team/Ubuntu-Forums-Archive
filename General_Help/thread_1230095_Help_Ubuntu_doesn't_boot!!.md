---
title: "Help Ubuntu doesn't boot!!"
date: 2009-08-03
forum: General Help
---

### Post by the2020 on 2009-08-03
Hey, 
I can't boot in to Ubuntu, the load screen and login screen are both messed up (graphic problem I think) I tried reconfiguring xorg a bunch of times and I tried the xfix in recovery mode. When it's loading the recovery mode it says something failed but I can't see what it is exactly because its going fast. 

Please helppp:(

---

### Post by Soul-Sing on 2009-08-03
> he recovery mode it says something failed

Is it possible to post that errormessage. Without errormessages it is al most impossible to tackle this problem/problems.

---

### Post by the2020 on 2009-08-03
how can I do that? it passes by so fast when its loading recovery mode. I know its possible I just don't know how.

---

### Post by metalf8801 on 2009-08-03
> **the2020 said:**
> Hey, 
 When it's loading the recovery mode it says something failed but I can't see what it is exactly because its going fast. 

Please helppp:(

Have you tried pressing Pause when the message shows comes up?

---

### Post by the2020 on 2009-08-03
I probably sound pretty stupid to you guys but which key is pause? P? hehe

edit: Sorry I see it up there beside scroll lock, ill try that and be back in a few minutes ;b

---

### Post by the2020 on 2009-08-03
Actually pause/unpause during boot is ctrl+s/ctrl+q

Ok so anyway, I wrote down the message on a piece of paper and here it is:

*Mounting local filesystems...
ntfs-3g:Failed to access volume '/dev/disk/by-uuid/0E309D3609D262D' No such file or directory

Please type '/sbin/mount.ntfs-3g --help' for more information

[15.115941] VFS: Can't find ext3 filesystem on dev sdb1.
wrong fs type, bad option, bad superblock on /dev/sdb1/, missing code page or helper program or other error


Hmmm this is very weird? how can it not recognize the ext3. A few weeks back, I reconfigured xorg for a new graphic card after I rebooted I received this problem and I tried all the repair options in the recovery mode and nothing worked so I just left it and used windows for the past 2 weeks.

---

### Post by the2020 on 2009-08-03
bumppp I miss ubuntu :(

---

### Post by tjwoosta on 2009-08-03
It looks like you have some configuration errors in your /etc/fstab.


It would be great if you could post the contents of the following commands

```
sudo gedit /etc/fstab
```

```
sudo fdisk -l
```

```
blkid
```

If you cant boot into ubuntu you could always use the live cd and mount your ubuntu partition from there to access the files

---

### Post by the2020 on 2009-08-03
Here is the contents of fstab(im in a livecd)

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc     defaults                             0  0  
# /dev/sda1
UUID=a9fd422a-13cf-4d5f-aa3b-80517f048bcc  /                 ext3     defaults,errors=remount-ro,relatime  0  1  
# /dev/sdb1
UUID=0E309D36309D262D                      /media/drv0       ntfs-3g  defaults                             0  0  
/dev/sdb1                                  /media/Storage    ext3     defaults,relatime                             0  0  
/dev/sda2                                  /media/Documents  ntfs     defaults                             0  0

---

### Post by the2020 on 2009-08-03
Ok I also dide those two commands in the live cd with everything mounted 

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a9fd422a-13cf-4d5f-aa3b-80517f048bcc" TYPE="ext3" 
/dev/sda2: UUID="E6D0EB47D0EB1D15" LABEL="Documents" TYPE="ntfs" 
/dev/sdb1: UUID="88C0E182C0E176BA" TYPE="ntfs" 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe39ae39a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3667    29455146   83  Linux
/dev/sda2            3668        5005    10747485    7  HPFS/NTFS

Disk /dev/sdb: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a52f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4110    33013543+   7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by tjwoosta on 2009-08-03
I dont know how it could have happened, but this part of your fstab is trying to mount /dev/sdb1 as an ext drive, when its really an ntfs drive. 

```
/dev/sdb1 /media/Storage ext3 defaults,relatime 0 0 
```


You dont have any swap partitions?  It only shows one ext3 drive (your linux partition) and two ntfs drives


Anyway I made some changes to your fstab that I think should work, first backup your existing fstab somewhere, then replace it with this one.  Read the comments I made, if your have any confusion.


```

#I commented out all of your old fstab lines because the UUID's and filesystem types dont match whats on your hard disk.

# <file system> <mount point> <type> <options> <dump> <pass>
# proc /proc proc defaults 0 0
# /dev/sda1
#UUID=a9fd422a-13cf-4d5f-aa3b-80517f048bcc / ext3 defaults,errors=remount-ro,relatime 0 1
# /dev/sdb1
#UUID=0E309D36309D262D /media/drv0 ntfs-3g defaults 0 0
#/dev/sdb1 /media/Storage ext3 defaults,relatime 0 0
#/dev/sda2 /media/Documents ntfs defaults 0 0 

proc /proc proc defaults 0 0

#/dev/sda1  (the only ext3 drive on your disk)
UUID=a9fd422a-13cf-4d5f-aa3b-80517f048bcc / ext3 defaults,errors=remount-ro,relatime 0 1

#/dev/sda2 (an ntfs drive)
UUID=E6D0EB47D0EB1D15 /media/Documents ntfs-3g defaults,locale=en_US.utf8  0 0


#/dev/sdb1 (an ntfs drive)
UUID=88C0E182C0E176BA /media/drv0 ntfs-3g defaults,locale=en_US.utf8  0 0


#if you have a cdrom and or dvdrom drive uncomment the two lines below

#/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
#/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0 


```

any lines that start with a # are commented out (meaning the machine wont read them). It is safe to remove them completely if you want, I only left them there so you can see what I did.



To be honest though, I dont think the misconfigured fstab was the reason your machine isn't starting.  The only drive that should really matter would be /dev/sda1 and that one was already configured properly.

You said you were reconfiguring xorg when things stopped working, so thats more likely to be the real problem.  If things still dont work after replacing the fstab I would try renaming /etc/X11/xorg.conf to something else like xorg.conf.backup and try booting without an xorg.conf (the newer versions of xorg dont actually require an xorg.conf to work, its basically only to optimize your graphics settings)

---

