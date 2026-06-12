---
title: "read-only spare hardrive on update.."
date: 2011-01-04
forum: General Help
---

### Post by davidbowie on 2011-01-04
Prior to the update my internal hd worked flawless. Now its a read-only disk and i can't change it by gui. I am a command line beginner and need some direction. Much appreciated! 

```
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
UUID=ec6a03df-4c12-426e-ad85-7d398d172b77 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

``````
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zak)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```:guitar:

---

### Post by ridgeland on 2011-01-04
Looks like /etc/fstab says if there is any error then mount the drive as read-only. errors=remount-ro

I use the same errors=remount-ro on my PC and it mounts as read-write.  Maybe you need some way to check the hard drive for errors.  fsck?  I don't know it so read 
$ man fsck
if you don't know it either.

If you want to experiment you could change errors=remount-ro to defaults
That would just ignore errors.  The errors could be a warning that your hard drive is nearing failure.

---

