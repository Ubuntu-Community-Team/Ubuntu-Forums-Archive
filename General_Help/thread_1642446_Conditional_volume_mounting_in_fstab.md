---
title: "Conditional volume mounting in fstab?"
date: 2010-12-10
forum: General Help
---

### Post by Objekt on 2010-12-10
I have an external hard drive that, when in use, I connect through eSATA.  Is there a way to have it mounted automatically at system startup, but only if it's present?

For now, my system gets hung up if the drive is disconnected or not powered on at startup.  I have to press "S" a couple of times to skip mounting the associated volume.  I'd rather have system startup able to complete without intervention, at least as far as me logging in.

Ideally, the system would wait some reasonable time - perhaps 15 seconds - and then skip mounting the disk.  So how do I do that?

Not sure whether it matters, but the external drive contains a single NTFS volume.  It is one of several NTFS volumes I maintain because I also run Windows XP at times (gasp!).  Here's my /etc/fstab contents.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5b5ce71f-d535-4e69-84b7-73f5a6959684 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=0ccd6493-eaa1-4932-8d19-ae9e25871f04 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=77bcb481-5b62-4062-bbc1-f1d68fbbe48c none            swap    sw              0       0
# swap was on /dev/sdc5 during installation
UUID=6af0cef2-ebe2-45b5-8f09-f05b2d8802cd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#new section for automounting NTFS volumes, copied from Ubuntu 9.10 installation
#mounting NTFS data partitions

#Storage
/dev/sda2 /media/Storage ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#OldWD (320 GB Western Digital drive)
UUID=B86C9ABE6C9A773A /media/OldWD ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#UbuntuStorage
#yet another for the new ext3 partition
UUID=d6dbe37d-d487-474d-9e14-9db95cb10297	/media/UbuntuStorage ext3 defaults 0 2

#storage partition on second 1 TB drive
UUID=30B1EA6105CD5A6E /media/MoreNTFS ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#Not Windows 
UUID=3C482AA9482A61BE /media/NotWin7 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

#external HDD
UUID=6A9065039064D75B /media/PieceOfJunk ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
```

---

