---
title: "A few problems with NTFS and FAT32 mounting"
date: 2006-06-24
forum: General Help
---

### Post by relinquish on 2006-06-24
Hello All,

I just installed Ubuntu 6.06, and I'm loving it so far.

Initially, gnome did not recognize my NTFS and Fat32 partitions, so I had to add the /etc/fstab entries myself. I did so, and managed to get Fat32 mounted. But NTFS I could only mount manually, using ntfs-fuse's ntfsmount, because of getting an error message when trying to mount from fstab.

The way I have it set up, I can access all of my files on both partitions, as well as write to both partitions. The only problem is that all files AND folders are set as executable (rwxrwxrwx).

The command I use to mount ntfs:
sudo ntfsmount /dev/hda1 /media/ntfs -o rw,umask=0

The /etc/fstab entry I use for fat32 mounting:
/dev/hdb1       /media/storezone vfat   rw,exec,uid=1000    0 0

So to sum up my problems:
1. How can I make NO files executable (or just .exes) on both partitions?
2. How can I mount my NTFS partition from fstab?

---

### Post by jhr79 on 2006-06-25
For the second question, copy of my current fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       /home           ext3    defaults        0       2[B]
/dev/hda1       /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0    1[/B]
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by relinquish on 2006-06-25
jhr79: Bear in mind that I'm mounting with rw access using ntfs-fuse.

---

### Post by retomi on 2007-03-12
I have the same problem :(

---

