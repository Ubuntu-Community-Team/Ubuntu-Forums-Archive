---
title: "cannot write to ext2"
date: 2006-04-26
forum: General Help
---

### Post by olsonar on 2006-04-26
I have an ext2 partition, and ubuntu will read from it fine, but only root can write to it. Is there any way to fix this problem? I've also been having wierd problems with fat32.

---

### Post by aysiu on 2006-04-26
Assuming your Ext3 partition is /dev/hda2 (I don't know where it is), try ```
sudo umount /dev/hda2
sudo mkdir /ext2
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` Add in this line (or replace whatever line refers to /dev/hda2 with this one) ```
/dev/hda2 /ext2 ext2 defaults 0 0
``` Save and ```
sudo mount -a
sudo chown -R olsonar:olsonar /ext2
sudo chmod -R 755 /ext2
```

For FAT32:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by olsonar on 2006-04-26
Thanks. That seems to have fixed the ext2fs problem, but I don't know about the FAT32. The problems I've been having with that don't make any sense to me. They're so erratic and infrequent enough that it's hard to tell just what is causing it. I'm not entirely sure what the problem is, even. All I know is that I lose files from it occasionally (I think it's when I reboot to windows). I've reforrmatted it, run scandisk on it in windows, but to no avail. It worked perfectly until a few weeks ago.

---

### Post by aysiu on 2006-04-27
Can you post the output of this command? ```
cat /etc/fstab
```

---

### Post by olsonar on 2006-04-27
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /media/bios     vfat    iocharset=utf8,umask=000        0 0
/dev/hda6       /media/dios     ext2    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I just changed the /dev/hda7 line. It didn't have the "iocharset=utf8" before. Maybe that's all I needed to do to fix it, but since I don't know exactly what's causing the problem, I don't know what to do to test it.

---

### Post by aysiu on 2006-04-27
Another thing you can try is mounting it to a static folder instead of a folder inside of /media or /mnt

Sometimes mounting inside /media causes weird things to happen.

Let me know if you need a step by step on static mount points.

---

