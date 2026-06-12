---
title: "unable to automount new partitions"
date: 2011-04-08
forum: General Help
---

### Post by ymp on 2011-04-08
I placed some new partitions in my hard disk but have been unable to write the correct entry in fstab to get them to automount. I can see them in nautilus and manually mount and use them, but I get failures when I try to add them to fstab, unsure what I am doing wrong.

I mounted two new partitions, one ext4 and one ntfs formatted partions.
The fstab file reads as follows
----------------
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
UUID=0d102e23-8006-4a4f-a007-ef97a9feaccb 	/media/data           ext4    defaults        0       1
UUID=615B763C5F4E8C00  	/media/data2          ntfs	defaults, users, umask=000,	0	0
UUID=0038fee5-baf1-4e8e-bd2e-28200b3f65de /home           ext2    defaults        0       2
UUID=4A78585A785846BB /windows        ntfs    defaults,users, umask=000, 0       0
UUID=dba35a41-8826-4675-bf74-d5fd8741cb8e none            swap    sw              0       0


I get the following failure from mount -a
-----------------
sudo mount -a
[mntent]: line 11 in /etc/fstab is bad
[mntent]: line 13 in /etc/fstab is bad
mount: special device UUID=0d102e23-8006-4a4f-a007-ef97a9feaccb does not exist


any assistance in figuring this out appreciated

---

### Post by falko on 2011-04-08
When you mount the partitions manually, run
```
mount
```
From the output you should be able to create the correct /etc/fstab entries.

---

### Post by ymp on 2011-04-08
mount gives me the following, unsure what to do with it

/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda7 on /home type ext2 (rw)
/dev/sda1 on /windows type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ymp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ymp)
/dev/sda8 on /media/7b8f07f9-76c6-4099-b42e-6d19ac52d0ac type ext4 (rw,nosuid,nodev,uhelper=udisks)

further advice appreciated

---

### Post by ymp on 2011-04-08
Resolved,
Although G Parted gave the disk address as hda, they only exist on the computer in /dev/sda, I can't explain that but I am sure someone who understands linux better than me would say 'of course'

once I figured that out they mounted

---

