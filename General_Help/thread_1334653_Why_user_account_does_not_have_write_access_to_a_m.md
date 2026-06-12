---
title: "Why user account does not have write access to a mounted"
date: 2009-11-22
forum: General Help
---

### Post by aminga on 2009-11-22
I have multiple hard drive in my PC with Ubuntu 9.10.  Grub is used for multi boot.

sda1   WinXP (ntfs)
sda2   data partition

sdb1   "/boot" (ext3)
sdb3   Temporary backup partition  (ext3)
sdb5   "swap"
sdb6   "/" Ubuntu 9.10  (ext4)

sdd1   External SATA drive (ext2)

I have set this in fstab
```

/dev/sda1   /mnt/WinXP_sda1  ntfs  rw,user,auto,exec,utf8  0  0
/dev/sda2   /mnt/osshare     ext3  defaults,user           0  0
/dev/sdb3   /mnt/sdb3        ext3  defaults,user           0  0
/dev/sdd1   /mnt/sdd1        ext2  defaults                0  0

```

This is the output of mount command
```

aminga@FatboyPC:~$ mount
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /proc/bus/usb type usbfs (rw,devgid=124,devmode=664)
/dev/sdb1 on /boot type ext3 (rw)
/dev/sda1 on /mnt/WinXP_sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /mnt/sdd1 type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aminga/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aminga)
/dev/sdb3 on /mnt/sdb3 type ext3 (rw,noexec,nosuid,nodev)
/dev/sda2 on /mnt/osshare type ext3 (rw,noexec,nosuid,nodev)
aminga@FatboyPC:~$ 

```

I can read and write to ntfs partition.
I can not write to sda2, sdb3, or sdd1.  Only root can.

sda2 (as osshare) is where I have all my data files, pictures, music, etc. so  want to ave access to them all the time.

1- Why I do not have write permission to sda2 and sdb3 and extrenal SATA drive sdd1?
2- How do I set them up in the fstab?

---

### Post by jm2 on 2009-11-22
Have you checked the file permissions, user, and owner of the /mnt/sshare?

ls -l /mnt/sshare

If the owner, and group are root, then that could be reason why others can't access this shared directory.

---

### Post by jm2 on 2009-11-22
Sorry... look at this thread

[http://ubuntuforums.org/showthread.php?t=1333807](http://ubuntuforums.org/showthread.php?t=1333807)

It seems to have the same issues as you.

---

### Post by aminga on 2009-11-24
Checking permissions for the directories that I made in "/mnt/" shows that they all have root as owner and group.
This is due to the fact that only root can make directory in "/mnt/".  I have not changed the permissions for the "/mnt/". It was generated that way during installation.

I followed the instructions in the link you listed, and still did not get write access to "/dev/sdd1" which is an external SATA drive.

For now, I changed the owner and group to myself so I can have write access to those partitions. There is user name aminga and a group aminga.  User aminga belongs to group aminga (this was automatically generated during OS install).

```

sudo chown -R aminga /mnt/osshare
sudo chgrp -R aminga /mnt/osshare

sudo chown -R aminga /mnt/sdd1
sudo chgrp -R aminga /mnt/sdd1

```
I know this is not a good solution in a multi-user environment, but I have not found any better way yet.

Thanks for your help.

---

