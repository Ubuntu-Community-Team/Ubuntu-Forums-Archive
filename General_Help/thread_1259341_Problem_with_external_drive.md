---
title: "Problem with external drive"
date: 2009-09-06
forum: General Help
---

### Post by taipan_snake on 2009-09-06
Hi all, I have a problem with my 20gb fat32 external drive (yes...it's very old)

Anyway, when I plug it in, nothing happens. The light on the drive turns on, but there's nothing in Ubuntu. Running "ls /media/" in the terminal only shows the cd drive.

Is anyone able to help? Thanks!

EDIT: The drive works perfectly in Windows.

---

### Post by NoaHall on 2009-09-06
You need to mount it. Try using "cat /etc/mtab" and "cat /etc/fstab" and posting the result here.

---

### Post by taipan_snake on 2009-09-18
Sorry for a late reply, i haven't been on my Ubuntu machine for about a week...

Anyway, "cat /etc/mtab" displays:

```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/david/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=david 0 0

```

And "cat /etc/fstab" displays:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4a52f0a2-5ec1-4e1c-8a90-9868b76f66d9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8112c189-afb9-4c3e-a1e2-ee3f97db3407 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Thanks for your help, but it seems none of the commands diplays anything to do with my external drive. But, thanks anyway!

---

