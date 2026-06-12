---
title: "HDD disappears, accessible via terminal"
date: 2010-08-08
forum: General Help
---

### Post by snakechaser on 2010-08-08
My Lacie NAS ("Network Space") quit working, so I took the drive from it  to recover my data. Filesystem is XFS. So I booted up the Ubuntu Live  CD. At first the drive was accessible, but a lot of important folders  weren't accessible because I had no rights. So I chmodded them, but  after that the drive became invisible.
I can access the drive via terminal, I've also copied some of the most important files already.
But I'd like to gain access via the normal file explorer, which makes copying a lot easier.
In accordance to [this thread]("http://ubuntuforums.org/showthread.php?t=1269178") I'll allready give some details:

> root@ubuntu:/home/ubuntu# mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb2 on /media/disk type xfs (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
> 
root@ubuntu:/home/ubuntu# sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C67EDD3B7EDD2549" LABEL="Door systeem gereserveerd" TYPE="ntfs" 
/dev/sda2: UUID="6222EB9322EB6B0D" TYPE="ntfs" 
/dev/sda3: UUID="A0B0EE48B0EE248E" TYPE="ntfs" 
/dev/sdb2: UUID="491521bf-8342-4464-b97e-c709c949a5cb" TYPE="xfs" 
/dev/sdb5: TYPE="swap" 
/dev/sdb7: UUID="1d8d769e-06c0-510e-48d4-89464c2ec68d" TYPE="mdraid" 
/dev/sdb8: UUID="740b2551-b053-a7be-45b8-00747ad72fc6" TYPE="mdraid" 
/dev/sdb9: UUID="619d39b7-e044-4a3e-8e66-3e71d6633504" SEC_TYPE="ext2" TYPE="ext3" 


> 
root@ubuntu:/home/ubuntu# cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0


Id really appreciate any help here :)

---

