---
title: "cannot see or mount JFS hardrive #2 after changing label..."
date: 2009-12-06
forum: General Help
---

### Post by killabee44 on 2009-12-06
Hi all,

Having some problems seeing a drive after I changed the label. This is on a Mythbuntu 9.10 install. The problem occurs on the storage drive sdb1. 

Here is some info:

cat /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=15443d9a-a030-4969-b569-a936c2a7ef74 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=ec39da7c-894d-436f-879e-6ebdc6b1cf4d /home           jfs     defaults        0       2
#1.5 TB DRIVE CONTAINS MYTH RECORDINGS, VIDEO LIBRARY, AND MUSIC VIDEOS
UUID=a92fcefc-1d43-485f-8d65-e6506ef6ac1c /mythtv         jfs      defaults       0       1 
# swap was on /dev/sdb2 during installation
UUID=ad917c40-3845-4259-88ca-eff4c0e6eb3e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


The line:

```
#1.5 TB DRIVE CONTAINS MYTH RECORDINGS, VIDEO LIBRARY, AND MUSIC VIDEOS
UUID=a92fcefc-1d43-485f-8d65-e6506ef6ac1c /mythtv         jfs      defaults     
```

is something I typed into the fstab when trying to fix the problem after much searching. Needless to say, it did not work.


sudo fdisk -l:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000207b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3831    30772476   83  Linux
/dev/sda2            7784       77825   562612365    5  Extended
/dev/sda3            3832        7783    31744440   83  Linux
/dev/sda5            7784       77825   562612333+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031b9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      181126  1454894563+  83  Linux
/dev/sdb2          181127      182401    10241437+  82  Linux swap / Solaris

```



df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              29G  2.2G   26G   8% /
udev                  2.0G  264K  2.0G   1% /dev
none                  2.0G     0  2.0G   0% /dev/shm
none                  2.0G  344K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             537G  147M  537G   1% /home
```


Thanks for any help you guys can give.

---

### Post by killabee44 on 2009-12-06
Ok, here is output of my:

sudo blkid:
```

/dev/sda1: UUID="15443d9a-a030-4969-b569-a936c2a7ef74" TYPE="ext4" 
/dev/sda3: UUID="2dfd438b-957d-403c-99c7-95fd6b44726c" TYPE="ext4" 
/dev/sda5: UUID="ec39da7c-894d-436f-879e-6ebdc6b1cf4d" TYPE="jfs" 
/dev/sdb1: LABEL="mythtv" UUID="38d70959-3e49-44a9-801b-cedd97e95a28" TYPE="jfs" 
/dev/sdb2: UUID="ad917c40-3845-4259-88ca-eff4c0e6eb3e" TYPE="swap" 


```

---

### Post by killabee44 on 2009-12-06
Something I found..

When I run Gparted to look at the drive I get an error: 

"Failed to mount "mythtv". The enclosing drive for the volume is locked."


What do you guys make of that?

*Edit*

Ok, it looks like during my attempts at fixing this issue I formatted the partition in question and that changed the UUID to: 38d70959-3e49-44a9-801b-cedd97e95a28. I updated the fstab and will reboot... fingers crossed.

---

### Post by killabee44 on 2009-12-06
Rebooted and now I get the following error as soon as Gparted opens:

"Failed to mount "mythtv"."

"You are not privileged to mount the volume "mythtv"."

It looks like I have some permission issues.

---

### Post by killabee44 on 2009-12-06
sudo mount -a:

```
mount: mount point /mythtv does not exist
```


Still cannot see the drive even from a sudo nautilus.

---

### Post by killabee44 on 2009-12-06
ls -lah /dev/disk/by-uuid:

```
total 0
drwxr-xr-x 2 root root 140 2009-12-06 21:16 .
drwxr-xr-x 6 root root 120 2009-12-06 21:16 ..
lrwxrwxrwx 1 root root  10 2009-12-06 21:07 15443d9a-a030-4969-b569-a936c2a7ef74 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-12-06 21:16 2dfd438b-957d-403c-99c7-95fd6b44726c -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-12-06 21:16 38d70959-3e49-44a9-801b-cedd97e95a28 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-12-06 21:07 ad917c40-3845-4259-88ca-eff4c0e6eb3e -> ../../sdb2
lrwxrwxrwx 1 root root  10 2009-12-06 21:07 ec39da7c-894d-436f-879e-6ebdc6b1cf4d -> ../../sda5
```

---

### Post by The Cog on 2009-12-07
> **killabee44 said:**
> sudo mount -a:

```
mount: mount point /mythtv does not exist
```


Still cannot see the drive even from a sudo nautilus.

That's quite a clear error message. Try making the mount point:
```
sudo mkdir /mythtv
sudo mount /mythtv
```

I notice the last two numbers on your fstab line for the mythtv partition are 0 1 - these should ideally be 0 2 instead. The root partition should be the only one marked as being pass 1. The pass argument controls the order in which fsck should run - root partition should be 1 and any others you want to check should all be 2.

---

### Post by Joeb454 on 2009-12-07
Moved to General Help @ OP request

---

### Post by killabee44 on 2009-12-07
> **The Cog said:**
> That's quite a clear error message. Try making the mount point:
```
sudo mkdir /mythtv
sudo mount /mythtv
```

I notice the last two numbers on your fstab line for the mythtv partition are 0 1 - these should ideally be 0 2 instead. The root partition should be the only one marked as being pass 1. The pass argument controls the order in which fsck should run - root partition should be 1 and any others you want to check should all be 2.

LOL... something so, so, simple... Well, I guess that's how you learn. Thanks!

Also, I will change the 1 to a 2... didn't notice that. What about the /home partition? Should that one also be a 2?

Edit, just researched and found that the /home should also be a "2". Much appreciated.

---

