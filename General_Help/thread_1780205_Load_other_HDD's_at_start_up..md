---
title: "Load other HDD's at start up."
date: 2011-06-11
forum: General Help
---

### Post by Rhetoric Camel on 2011-06-11
When I load up Ubuntu and I open any of my music players and click on a song in the library the song wont load until I go into Places>(hdd with music)
Is there any way I can load this hard drive and the other hard drive I have without having to first open in in the Places menu? The same problem goes for pictures I have stored on another hdd. I can't load them in Picasa until I have first opened the hard drive through the Places menu. I would like these to be read from start up so that I can skip this step.

---

### Post by TeoBigusGeekus on 2011-06-11
Mount the disks and post us the output of
```
df -h
sudo fdisk -l
mount
sudo blkid
```
Don't forget to tell us which of these disks you want mounted.

Then post us the contents of your fstab file
```
gksu gedit /etc/fstab
```

---

### Post by Rhetoric Camel on 2011-06-12
I would like the two hdd's labeled Second HDD, and For Programs to load up when I boot my computer.



:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             101G   33G   63G  35% /
none                  1.6G  372K  1.6G   1% /dev
none                  1.6G  396K  1.6G   1% /dev/shm
none                  1.6G  260K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
/dev/sr0              676M  676M     0 100% /media/PSP3
/dev/sdb1             197G  184G   13G  94% /media/Second HDD
/dev/sda2             250G  241G  8.9G  97% /media/For Programs

:~$ sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6cdf6cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38913   261369517+   7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe794ac88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25605   205672131    7  HPFS/NTFS
/dev/sdb2           25606       38913   106896510   83  Linux

:~$ mount
/dev/sdb2 on / type ext3 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/rhetoriccamel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rhetoriccamel)
/dev/sr0 on /media/PSP3 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1 on /media/Second HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/For Programs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

:~$ sudo blkid
/dev/sda1: UUID="76C49467C4942B7F" TYPE="ntfs" 
/dev/sda2: LABEL="For Programs" UUID="488CCED98CCEC124" TYPE="ntfs" 
/dev/sdb1: LABEL="Second HDD" UUID="B2E0BED6E0BE9FD1" TYPE="ntfs" 
/dev/sdb2: LABEL="Ubuntu 10.04" UUID="e575e192-7cce-4709-8dc3-ce2309fa8f90" TYPE="ext3" 
:~$ 

:~$ gksu gedit /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 /               ext3    errors=remount-ro 0       1
/mnt/512.swap non swap sw 0 0

---

### Post by oldfred on 2011-06-12
I prefer not to use spaces in folder or file names. You can use CamelCase, under_score, just oneword. Often in Linux you then have to put the "name with spaces" in quotes so the command knows it is one word.

You have to make a mount point, set permissions (if not a windows format), and mount partition. When you click on a partition this is done automatically with defaults.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Also where do you want to mount. /media is really intended for temporary mounts of removable devices. You can use that, you can mount directly into /home or mount somewhere else and link back to /home. Unmount your current mounts before doing this so there are not conflicts:

This would be in /home, use your username in place of username in all of below:
sudo mkdir /home/rhetoriccamel/SecondHDD
or 
sudo mkdir /home/rhetoriccamel/"Second HDD" # I think this works but I do not use spaces. Then you have to use it with quotes eveywhere else below as mount points must exist before fstab is used.

sudo mkdir /home/rhetoriccamel/programs

Paste this into your fstab:

sudo gedit fstab
```
# Entry for /dev/sdb2 :
UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 /home/rhetoriccamel/programs ext3 auto,users,rw,relatime 0 2
# Entry for /dev/sdb1 :
UUID=B2E0BED6E0BE9FD1 /home/rhetoriccamel/SecondHDD ntfs-3g defaults 0 0
```After any edits to fstab always remount to make sure there are no editing errors. You must fix errors before rebooting.

sudo mount -a
if it just returns it remounted everything & worked. I often get the mount does not exist as I forget to create mount before editing or have typo in name of mount point.

You cannot change permissions & ownership of your NTFS partition, but can on your ext3 partition. 
If issues 777 is most permissive you can have:
echo $USER
sudo chmod -R 777 /home/rhetoriccamel/programs
sudo chown -R $USER:$USER /home/rhetoriccamel/programs

Your partitions are getting very full. In NTFS, it normally wants at least 20% free. If just reading you may be ok, but if deleteing & adding then it will get very slow or even stop working. You ext3 partition is also getting full. Linux hides 5% typically to prevent crashes but still will slow down and start fragmenting if too little space left.

---

### Post by grahammechanical on 2011-06-12
This link might help.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I have not tried this myself (although I am thinking of using it to automount two other partitons on my one hard disc). I found this when searching for an answer to this question that someone else had posted.

Regards

---

