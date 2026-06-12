---
title: "Can not mount USB on Maverick"
date: 2011-01-30
forum: General Help
---

### Post by Baharmur on 2011-01-30
Hello,

I have just installed Ubuntu 10.10 and it does not mount usb sticks. Simply nothing happens when i connect a flash disk. Through "disk utility", i can see the device, and it is named /dev/sdb1. When i click "mount", however, it says: 

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

Is there a solution to this problem?
Thank you!

---

### Post by quadproc on 2011-01-30
> **Baharmur said:**
> Hello,

I have just installed Ubuntu 10.10 and it does not mount usb sticks. Simply nothing happens when i connect a flash disk.
I am also running 10.10 but with all updates available as of late January and what I see when I plug in a USB stick is a new icon appears on the desktop which is identified as "4.0 GB Filesystem"; there is no other indication of the USB stick having become present.

When I use a terminal and type "mount" I see all the usual things plus /dev/sdh1 on /media/DB70-0B5E type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

It sounds like either your system is working correctly and that you did not notice the desktop icon, or that something is not right with your system software.  In the latter case, you might find that the updates will fix it.  Of course, it is possible that updates will break your system so I suggest appropriate caution.

quadproc

---

### Post by Baharmur on 2011-01-31
Thank you for the reply. 
All the updates are complete but unfortunately i still can't see the icon. When i type "mount" in terminal, i see this:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bahar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bahar)

I also have usbmount installed, but that doesn't work either...

---

### Post by tredegar on 2011-01-31
Please plug in the stick and then post the output of the following commands
```
cat /etc/fstab
sudo fdisk -l
mount
```

---

### Post by Baharmur on 2011-01-31
Here is the output of commands. Hope it helps...

bahar@bahar:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0136711d-81a5-425d-9a8d-c8d7a394d763 none            swap    sw              0       0
bahar@bahar:~$ sudo fdisk -l
[sudo] password for bahar: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e72e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2087 MB, 2087714816 bytes
20 heads, 19 sectors/track, 10730 cylinders
Units = cylinders of 380 * 512 = 194560 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4       10731     2038028    6  FAT16
bahar@bahar:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bahar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bahar)
bahar@bahar:~$

---

### Post by tredegar on 2011-01-31
Thank you.
Please post code in CODE tags next time (Click go advanced, then the # icon)

It's a mess:
```
bahar@bahar:~$ mount
/dev/sd[COLOR="Red"]a[/COLOR]1 on / type ext4 (rw,errors=remount-ro,commit=600)

```
So /dev/sd[COLOR="Red"]a[/COLOR]1 is mounted as /

```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sd[COLOR="Red"]b[/COLOR]1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb5 during installation
UUID=0136711d-81a5-425d-9a8d-c8d7a394d763 none swap sw 0 0

```
But fstab says to mount dev/sd[COLOR="Red"]b[/COLOR]1 as root!

This does not make sense, your system should not be able to boot.

Find out the UUID of /dev/sd[COLOR="Red"]a[/COLOR]1 with **sudo blkid**
change the line in fstab from
```
/dev/sdb1 / ext4 errors=remount-ro 0 1
```
to
```
UUID=*uuid_of_dev/sd[COLOR="Red"]a[/COLOR]1* / ext4 errors=remount-ro 0 1
```

reboot.

---

### Post by Baharmur on 2011-01-31
Thank you very much!
Now i can see the icon when i connect the USB stick. I can not directly open it form desktop icon, though, i have to go to file system to see and reach what's inside. When i connect my USB external disk, i don't see the icon on desktop but when i go to file system, i can see and reach the files anyway. 
So that solves my mount problem.
Thanks again...

---

### Post by bear672 on 2011-08-02
> **tredegar said:**
> 

Find out the UUID of /dev/sd[COLOR="Red"]a[/COLOR]1 with **sudo blkid**
change the line in fstab from
```
/dev/sdb1 / ext4 errors=remount-ro 0 1
```
to
```
UUID=*uuid_of_dev/sd[COLOR="Red"]a[/COLOR]1* / ext4 errors=remount-ro 0 1
```

reboot.

How do you change the line in fstab? I followed this post this far but I don't understand where to change the line . . .

---

### Post by tredegar on 2011-08-02
@bear672

For God's sake, please stop Private Messaging me. Two already within 3minutes of each other.

I have a real life. I am busy with it. I am a volunteer here, not your paid servant.

You have ten posts here in 15 months and you expect a reply within *minutes*?

What planet are you from?

---

