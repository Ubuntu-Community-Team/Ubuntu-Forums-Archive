---
title: "Storage Device Manager Pysdm Problem"
date: 2011-07-14
forum: General Help
---

### Post by kamaro on 2011-07-14
Hello guys,..
I new to ubuntu, found it really good...but i've got problem here, another "pysdm" problem,..
The storage device manager "pysdm" is searching for partition on boot which's not exist. First, the usb drive (why shoud this thing searching for a removable drive?) and then the newly formated partition (splited volume) on my internal harddrive, now i've to press S to skip this checkup thing on boot. Yes we know this thing cost alot of booting time. 
I tried to remove this then install it again, refresh, same old problem. 

So, how to remove this pysdm and disable this automount feature?

Thank you...


*English isn't my native language so please be understandable. :)

---

### Post by dino99 on 2011-07-14
mountall deals with dynamic needs, so you dont need to worry. But your /etc/fstab might be borked:

sudo gedit /etc/fstab

you only need these lines:
- swap
- /home

comment out all the others (# at the line beginning)

example, mine is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	2
#Entry for /dev/sdc3 :
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523	/home	ext3	defaults,relatime	0	2

#Entry for /dev/sdc2 :
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16	none	swap	sw	0	0

of course yours have to use your uuid (done by: sudo blkid)

---

### Post by kamaro on 2011-07-14
Thank you dino99 for the reply
Well here's the fstab report
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  nodev,noexec,nosuid                  0  0  
/dev/sda8  /            ext2  errors=remount-ro,user_xattr,noauto  0  1  
/dev/sda5  /media/sda5  ntfs  defaults                             0  0  
/dev/sda6  /media/sda6  ntfs  defaults                             0  0  
/dev/sda7  /media/sda7  ntfs  defaults                             0  0  
/dev/sda9  /media/sda9  ext4  defaults                             0  0  
/dev/sdc5  /media/sdc5  vfat  noauto                               0  0  
/dev/sda3  /media/sda3  ext4  defaults                             0  0  
/dev/sda4  /media/sda4  ext4  defaults                             0  0  
/dev/sdb5  /media/sdb5  vfat  defaults                             0  0  
```

were sda8 is ubuntu (why error?),...and sda9 is not exist anymore, and the sdc5 and sdb5 is the usb drive. I cant see the line mentioned,..

Thanks

---

### Post by Silambarasan on 2011-07-16
[COLOR=Navy]Hi **dino99**, Thank you so much,

your post helped me much more. Actually I installed Pysdam(Storage device Manager ) after that eclipse (Java development editor) can't use other drives. now It's working fine, Thank you so much.

:D
[/COLOR]

---

