---
title: "Unable to change drive properties"
date: 2011-12-19
forum: General Help
---

### Post by baijopjoy on 2011-12-19
Hello every one,
Please help.
I am facing a problem of unable to change drive properties. the partitions which are common for windows and ubuntu, now appear as file access only. It's not allowing to create or delete a file. when I am trying to change drive property, it shows the error message "The permissions could not be changed. Sorry, could not change the permissions of "4CDA2D15DA2CFD38": Error setting permissions: Read-only file system"
please help,

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda7 during installation
UUID=159555d1-d19f-4089-af34-6968b93e5c21 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda8 during installation
UUID=cf50cb77-ec8b-443c-81c3-5d9b835162df none swap sw 0 0



the drives were working properly on Saturday

---

### Post by searchfgold6789 on 2011-12-19
>  the partitions which are common for windows and ubuntu, now appear as file access only.Sounds to me like you have some data partitions that are NTFS or FAT. Please post back your /etc/fstab file.

---

### Post by baijopjoy on 2011-12-19
i don't know how to get /etc/fstab

---

### Post by MartijnNL on 2011-12-19
Press Alt + F2 and run:

```
gedit /etc/fstab
```

That opens the file in a text-editor.

---

### Post by coffeecat on 2011-12-19
> **baijopjoy said:**
> i don't know how to get /etc/fstab

Open a terminal, and:

```
cat /etc/fstab
```

Highlight the output, right-click -> copy and then paste it into your post.

Are you mounting the partitions from the file manager? If so, mount them and post the output of this terminal command:

```
mount
```

Also, check that you have the package ntfs-3g installed. If it isn't (it should be), install it.

---

### Post by baijopjoy on 2011-12-19
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=159555d1-d19f-4089-af34-6968b93e5c21 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=cf50cb77-ec8b-443c-81c3-5d9b835162df none            swap    sw              0       0

---

### Post by baijopjoy on 2011-12-19
this drives were working normal till saturday

---

### Post by WorMzy on 2011-12-19
Make sure you have ntfs-3g installed.

---

### Post by coffeecat on 2011-12-19
> **baijopjoy said:**
> this drives were working normal till saturday

Your /etc/fstab file shows that you are not using fstab to mount the partitions common to Windows and Ubuntu. We're all having to assume that these are NTFS or FAT32, but without more information it is impossible to be sure and it is difficult to help you.

Please post the output of the "mount" command that I suggested and post the output of:

```
sudo fdisk -lu
```

---

### Post by WorMzy on 2011-12-19
> **coffeecat said:**
> Your /etc/fstab file shows that you are not using fstab to mount the partitions common to Windows and Ubuntu. We're all having to assume that these are NTFS or FAT32, but without more information it is impossible to be sure and it is difficult to help you.

Please post the output of the "mount" command that I suggested and post the output of:

```
sudo fdisk -lu
```
With a UUID like the one baijopjoy posted, it's almost certainly a ntfs partition.

---

### Post by coffeecat on 2011-12-19
> **WorMzy said:**
> With a UUID like the one baijopjoy posted, it's almost certainly a ntfs partition.

Agreed, but it would be nice to see more information. :)

---

### Post by baijopjoy on 2011-12-19
> **coffeecat said:**
> Open a terminal, and:

```
cat /etc/fstab
```

Highlight the output, right-click -> copy and then paste it into your post.

Are you mounting the partitions from the file manager? If so, mount them and post the output of this terminal command:

```
mount
```

Also, check that you have the package ntfs-3g installed. If it isn't (it should be), install it.


/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/baijo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=baijo)
/dev/sda1 on /media/4CDA2D15DA2CFD38 type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda5 on /media/8C888E52888E3AAA type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

---

### Post by baijopjoy on 2011-12-19
> **coffeecat said:**
> Your /etc/fstab file shows that you are not using fstab to mount the partitions common to Windows and Ubuntu. We're all having to assume that these are NTFS or FAT32, but without more information it is impossible to be sure and it is difficult to help you.

Please post the output of the "mount" command that I suggested and post the output of:

```
sudo fdisk -lu
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           96390   109103922    54503766+   7  HPFS/NTFS/exFAT
/dev/sda2       109105150   312576704   101735777+   f  W95 Ext'd (LBA)
/dev/sda5       138512493   306277620    83882564    7  HPFS/NTFS/exFAT
/dev/sda6       306279288   312576704     3148708+  dd  Unknown
/dev/sda7       109105152   136447999    13671424   83  Linux
/dev/sda8       136450048   138510335     1030144   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by coffeecat on 2011-12-19
Here's your problem:

> **baijopjoy said:**
> 
/dev/sda1 on /media/4CDA2D15DA2CFD38 type [COLOR="Red"]ntfs[/COLOR] (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda5 on /media/8C888E52888E3AAA type [COLOR="Red"]ntfs[/COLOR] (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

If you had the ntfs-3g driver installed, that output would have said "fuseblk" where I've highlighted in red. Your system is defaulting back to the read-only kernel ntfs driver. 

[quote="baijopjoy"]this drives were working normal till saturday [/quote]

Then you must have uninstalled ntfs-3g on Saturday, even if accidentally. By the way, both WorMzy and I had already suggested that you check to see if ntfs-3g is installed. You did not respond to this. Install ntfs-3g (it will remove ntfsprogs if you have this installed) and your problem will be resolved.

---

### Post by baijopjoy on 2011-12-19
> **coffeecat said:**
> Here's your problem:



If you had the ntfs-3g driver installed, that output would have said "fuseblk" where I've highlighted in red. Your system is defaulting back to the read-only kernel ntfs driver. 



Then you must have uninstalled ntfs-3g on Saturday, even if accidentally. By the way, both WorMzy and I had already suggested that you check to see if ntfs-3g is installed. You did not respond to this. Install ntfs-3g (it will remove ntfsprogs if you have this installed) and your problem will be resolved.

how i can check ntfs-3g is installed? and if it's not how i can install it

---

### Post by coffeecat on 2011-12-19
> **baijopjoy said:**
> how i can check ntfs-3g is installed? and if it's not how i can install it

You've tagged this thread "Lubuntu". If you are indeed running Lubuntu, use the Synaptic Package Manager. If Ubuntu 11.10, use the Ubuntu Software Centre.

---

### Post by baijopjoy on 2011-12-19
> **coffeecat said:**
> You've tagged this thread "Lubuntu". If you are indeed running Lubuntu, use the Synaptic Package Manager. If Ubuntu 11.10, use the Ubuntu Software Centre.

Sorry for the confusion, i'm using ubuntu 11.10

i installed ntfs-3g using software centre. but now also the problem persists.
so after running the mount command i got this reply


/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/4CDA2D15DA2CFD38 type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sda5 on /media/8C888E52888E3AAA type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
gvfs-fuse-daemon on /home/baijo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=baijo)

---

### Post by WorMzy on 2011-12-19
The problem will persist until you unmount, then remount, the partition.

```
udisks --unmount /dev/sda1
udisks --mount /dev/sda1
```

Repeat with sda5.

---

### Post by baijopjoy on 2011-12-19
> **WorMzy said:**
> The problem will persist until you unmount, then remount, the partition.

```
udisks --unmount /dev/sda1
udisks --mount /dev/sda1
```

Repeat with sda5.

thanks people....
a big big thanks....

---

### Post by baijopjoy on 2011-12-19
Thanks coffeecat and WorMzy.
I was even thinking about removing ubuntu, and going back to windows....
thanks........
:popcorn::KS):P:D:p

---

