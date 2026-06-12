---
title: "/etc/fstab empty"
date: 2009-08-10
forum: General Help
---

### Post by nixguru on 2009-08-10
I'm not quite sure how this happened, but apparently my /etc/fstab is empty, as is the backup file.   Has anyone else seen this as a result of an upgrade to 9.04 or anything like that?

The system seems to boot fine, but I really would like to get an fstab file rebuilt.  Can someone post me a generic /etc/fstab from a 9.04 install?  I will of course modify this for my own system, but I am at a loss how the system can manage to operate so well with just the UUID specification for root in the grub configuration file.

Here is my /etc/mtab:

```
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mikeb/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mikeb 0 0

```As you can see, no disk device is ever referenced here -- only rootfs.

I did see a few other people talk about having nothing in their fstab file, but I don't think there was any official explaination for it.  I'm sure I didn't clear the file out, although I suppose something bad could have happened after I converted the file system to ext4 from ext3.  Anyway, I have backed up all my files, reformatted the file system to ext3, and restored because I ran into another problem that seemed to be ext4 related.

Also, I noticed after writing this that there is no swap anymore.  Could explain the once in a while lockups.. :)

Thanks!

---

### Post by Barafu Albino Cheetah on 2009-08-10
What for do you need some genric fstab? It depends on your system. 
Just write it back manually, it is not a problem. 
```
barafu@shamaniak:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=08979dbe-26ab-4364-b3fb-a851e2789115 /               reiserfs relatime        0       1
# /boot was on /dev/sda2 during installation
UUID=2f9de0c4-dc0d-4b86-abf0-4a3ad87befbd /boot           ext2    relatime        0       2
# /windows was on /dev/sda1 during installation
UUID=782645D726459752 /windows        ext3    defaults, 0       1
# swap was on /dev/sda3 during installation
UUID=b25e49f8-d70e-4ed8-b3f4-5aa9ee59fb3b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by bageh on 2010-07-30
Same problem here: the crap of liblexz600core0 did something - a bug with usb mounting or something - and now my partitions can't mount with the session login.
If I click in the items, they are mounted at strange places, like those showed with mount command:
bageh@bageh-laptop:/$ mount
/dev/sda7 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
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
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bageh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bageh)
/dev/sda1 on /media/0E68523E6852252D type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3 on /media/472C-F707 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5 on /media/6107b328-bc77-4575-9577-3acc1965e203 type ext3 (rw,nosuid,nodev,uhelper=udisks)

I've looked upon fstab and guess what? It's empty!!!

---

