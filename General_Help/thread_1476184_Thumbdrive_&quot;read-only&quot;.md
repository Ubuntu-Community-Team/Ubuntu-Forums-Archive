---
title: "Thumbdrive &quot;read-only&quot;"
date: 2010-05-07
forum: General Help
---

### Post by dsmithnc on 2010-05-07
I have searched and read several posts that seem to apply, but I've not been able to solve the problem.

I have a usb stick that contains all my email files.  I need to delete a file from it, but every time I try I get "read-only file system.  No sudo chmod commands will work.

I'm using Lucid on an 64 bit machine.  It was ok yesterday but not today.

Thanks

****

---

### Post by WorMzy on 2010-05-07
Have you made an entry in fstab for it? If not, open /etc/mtab and see if it's been mounted with ro. If it is, just make an entry in fstab with the ro argument removed, then remount the drive.

Also, check that you haven't flipped a switch on the thumbdrive. I think some come with the option of "locking" the contents, making them read-only on a hardware level.

---

### Post by Maheriano on 2010-05-07
1. Check and make sure the little slider piece which determines readability is in the right position. Most thumb drives don't have one but some do. And all flash cards do.

2. Make sure it wasn't formatted read only.

---

### Post by dsmithnc on 2010-05-07
> **WorMzy said:**
> Have you made an entry in fstab for it? If not, open /etc/mtab and see if it's been mounted with ro. If it is, just make an entry in fstab with the ro argument removed, then remount the drive.

Also, check that you haven't flipped a switch on the thumbdrive. I think some come with the option of "locking" the contents, making them read-only on a hardware level.

No lock tab on this thumb drive.

Contents of Mtab:
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/****/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=**** 0 0
/dev/sdc1 /media/EMAIL vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

Looks like the thumbdrive is mounted 'rw'.

Here is content of fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c53467ce-2e7d-47c9-a566-9d2c0874178e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=8c9c1cf6-b903-4d5b-abe5-8a70f13f11a7 none            swap    sw              0       0

Thanks for the tip.

****

---

