---
title: "Flash Drive on old computer"
date: 2009-11-20
forum: General Help
---

### Post by treehouse on 2009-11-20
I'm trying to get some data off of my friend's flash drive. I have really old hardware, like pre-USB-2.0 type stuff. My hard drives are on IDE channels. When I insert the flash drive into either of my USB ports, nothing new automatically mounts, and my mtab file does not change at all. The only advice that I've seen on manually mounting a drive on USB suggests mounting /dev/sda1, but that's my IDE hard drive.

Here's my mtab:
```

nicholas@nicholas-desktop:~$ cat "/etc/mtab"
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-15-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb1 /hdb ext2 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/nicholas/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=nicholas 0 0
/dev/scd1 /media/030518_2309 iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0

```

Here's my fstab:
```

nicholas@nicholas-desktop:~$ cat "/etc/fstab"
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ff1e312d-7673-4676-85e6-828073d744a8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=bbab9e39-2084-4229-ba75-324e9031908b none            swap    sw              0       0
# /dev/hdb1
UUID=57cda58d-bcb8-4893-8bbc-75ef6ec4f31d /hdb            ext2    defaults,relatime     0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

How do I mount this drive?

---

### Post by undecim on 2009-11-20
Make sure that the drive is being detected. In a terminal, type "lsusb" and see if it lists the drive.

---

### Post by untappedpilot2 on 2009-11-20
Here's a link to a thread I started when I had a similar problem some time ago when I was trying to read one of my laptop HD through a USB adapter. Take a look this should help you. 

[http://ubuntuforums.org/showthread.php?t=1006874]("http://ubuntuforums.org/showthread.php?t=1006874")

---

### Post by treehouse on 2009-11-20
> **undecim said:**
> Make sure that the drive is being detected. In a terminal, type "lsusb" and see if it lists the drive.

Nothing even with the verbose flag. Does this mean my USB doesn't work at all?

---

