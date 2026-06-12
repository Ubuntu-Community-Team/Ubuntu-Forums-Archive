---
title: "An error occurred while mounting static"
date: 2011-03-24
forum: General Help
---

### Post by Coastalguy on 2011-03-24
I have been trying to mount a Windows NTFS partition in /etc/fstab. I had it working, but could not get mysql to start when adding a datadir setting in my.cnf. Following comments to change some of the mount options, I started getting the error "An error occurred while mounting static" on bootup. 

To see if it was this mounting entry, I commented it out and re-booted, but I am still getting the error. Although I didn't change any of the other fstab entries, I'm wondering if something is now wrong with one of the existing mounts.

re-activating the mount for my Windows NTFS partition, although I still get the error, passing it with the "S" and logging in, I see that my partition is mounted ok under My Computer. If anyone can see what might be wrong, I have provided my fstab file and the results of the mount command:

fstab entries (the last one is my Windows NTFS partition):

 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=9a1ee995-598a-444a-b58e-6c6f44c43fa7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb9 during installation
UUID=24e29c08-50e1-428b-a35f-df9802847e7c /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=a004bf57-c234-4416-b30c-3a9a6a56a859 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Mount /media/Sokkit ntfs partition
UUID=5B5E726C8F1D8D64 /media/Sokkit ntfs defaults,auto,uid=1000,gid=1000,unmask=002 0 0 

from mount command:

/dev/sdb8 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb9 on /home type ext4 (rw,commit=0)
/dev/sda6 on /media/Sokkit type fuseblk (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave0judy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave0judy)
/dev/sdc1 on /media/BACKUPS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

Thanks,

---

