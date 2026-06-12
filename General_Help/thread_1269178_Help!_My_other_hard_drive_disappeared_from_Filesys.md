---
title: "Help! My other hard drive disappeared from Filesystem?"
date: 2009-09-17
forum: General Help
---

### Post by rob86 on 2009-09-17
I have two drives. One (sda) is NTFS with WinXP and a lot of important stuff from my windows days. The other (sdb) is Ext3 with Ubuntu on it. Ever since I installed Ubuntu, I've been able to see and access the drive with windows (sda), but I just noticed tonight that it's disappeared. I tried to boot up windows, and it had to run chkdisk, and then WinXP booted up okay. I thought chkdisk would fix it, but I'm back on Ubuntu and it's still missing. 

Can anyone help me? This is a pretty serious problem, I access the files on that drive a lot! Plus, i'm a bit worried I damaged the files by accessing them on linux. 

Here's the output from fdisk -l. It sees the drive there, apparently.... 

```
rob@rob-desktop:~/ess$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d4c4d4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3160749

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2382    19133383+  83  Linux
/dev/sdb2            2383        2491      875542+   5  Extended
/dev/sdb5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sde: 513 MB, 513277952 bytes
16 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 992 * 512 = 507904 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001    c  W95 FAT32 (LBA)

```

---

### Post by scragar on 2009-09-17
```
mount
``````
sudo blkid
```and```
cat /etc/fstab
```Output all three please.

EDIT: to explain myself the first one is to see if the drive is mounted, but you don't know the mount point, the second is to find the block ID of the devices that are causing the problem, and the last one is to find out what your current automount config looks like so I can tell you how to edit it.

---

### Post by rob86 on 2009-09-17
Here it is...

```
rob@rob-desktop:~/ess$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sdg1 on /media/LACIE type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)
/dev/sde on /media/disk type vfat (ro,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)
```

```
rob@rob-desktop:~/ess$ sudo blkid
/dev/sda1: UUID="0EC86536C8651D69" LABEL="Main HD" TYPE="ntfs" 
/dev/sdb1: UUID="332b903f-5719-4679-bf18-bacd413e8cf2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="89180ead-dd80-47d5-9cb6-49754be8e9c0" 
/dev/sde: SEC_TYPE="msdos" UUID="18D0-0755" TYPE="vfat" 
/dev/sdg1: LABEL="LACIE" UUID="6853-5BA9" TYPE="vfat" 

```

```
rob@rob-desktop:~/ess$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=332b903f-5719-4679-bf18-bacd413e8cf2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=89180ead-dd80-47d5-9cb6-49754be8e9c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```


> **scragar said:**
> ```
mount
``````
sudo blkid
```and```
cat /etc/fstab
```Output all three please.

EDIT: to explain myself the first one is to see if the drive is mounted, but you don't know the mount point, the second is to find the block ID of the devices that are causing the problem, and the last one is to find out what your current automount config looks like so I can tell you how to edit it.

---

### Post by scragar on 2009-09-17
I'm assuming the first partition is what's not showing up, since everything else is mounted as far as I can tell.
First, we try to add it to the config:
```
sudo su
mkdir /media/**mount_point**
echo "UUID=0EC86536C8651D69 /media/**mount_point** auto users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 1" >> /etc/fstab
```
mount_point can be replaced for anything you want(as long as it doesn't have spaces in it), and it will appear on the desktop under that name(when mounted anyway).
Next try mounting it:
```
mount /dev/sda1
```
If that works we're all done, if not please share the error message.

---

### Post by rob86 on 2009-09-17
I think it worked, I can access the drive now. This was the output

root@rob-desktop:/home/rob/ess# mount /dev/sda1
The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.
root@rob-desktop:/home/rob/ess# 

Is that good? Fixing is pretty vague about what it's doing! 

What do you think caused this problem anyway? Something getting corrupted on the drive from me saving a file on it created in Ubuntu?

---

### Post by scragar on 2009-09-17
It probably just wasn't unmounted cleanly last time it was used so the lock remained on the file. It shouldn't be a problem now though.

---

### Post by rob86 on 2009-09-17
Well anyway thanks for the help

---

### Post by rob86 on 2009-09-18
By the way, how can I change the name "Mount_point" to something else? Without re-doing the stuff you told me to do I mean, if that's possible.

---

### Post by scragar on 2009-09-18
It's not all that easy, you need to edit /etc/fstab as root and remount the partition.
```
sudo gedit /etc/fstab
mount -o remount,rw /dev/sda1
```

---

### Post by rob86 on 2009-09-18
rob@rob-desktop:~/ess$ sudo mount -o remount,rw /dev/sda1
mount: you must specify the filesystem type

---

### Post by scragar on 2009-09-18
Erm, that's strange. Try doing it in two steps:
```
umount /dev/sda1
mount /dev/sda1
```

---

### Post by rob86 on 2009-09-18
I changed mount_point to "mainhd" in the fstab earlier, this is what happens when I try mounting it:

rob@rob-desktop:$ sudo mount /dev/sda1
fuse: failed to access mountpoint /media/mainhd: No such file or directory

---

### Post by scragar on 2009-09-18
Oh, poopy, knew I forgot something.
```
sudo mv /media/{mount_point,mainhd}
```
EDIT: {} are expansion operators, that line is the same as:```
sudo mv /media/mount_point /media/mainhd
```it's just a comma separated list of values to expand the argument out to(and it's a lot less typing, a lot harder to make mistakes, and a lot more fun to play around with :p).

---

### Post by rob86 on 2009-09-18
Nevermind, I had to mkdir /media/mainhd. I guess it works now.....

---

### Post by rob86 on 2009-09-18
Whoops, I didn't see your last reply. I did that mv anyway incase the mkdir wasn't enough. Thanks again!

---

### Post by scragar on 2009-09-18
For reference I wrote a script to move mount points, if it's any use to ya.
```
#!/bin/bash

FROM=$1
TO=$2 ## lol, to=2 :p
PATH=$(mount | grep "$1" | awk '{ print $1 }');

umount $PATH
rmdir /media/$FROM

cp /etc/fstab{,_backup}
sed "s/$FROM/$TO/" /etc/fstab_backup > /etc/fstab

mkdir /media/$TO
mount $PATH
```
first make it exectuable:
```
chmod +x script.sh
```
Then use it:```
sudo script.sh mount_point mainhd
```:p

---

### Post by rob86 on 2009-09-18
Neat script, but what's the sed do? Stream editor? I don't understand that line at all. I liked the to $2, too.

---

### Post by scragar on 2009-09-18
sed is stream editor, so that part means:
```
s/          replace
$FROM
/                 with
$TO
/                 end replace
```

---

