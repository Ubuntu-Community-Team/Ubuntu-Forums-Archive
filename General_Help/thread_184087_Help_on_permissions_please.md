---
title: "Help on permissions please"
date: 2006-05-29
forum: General Help
---

### Post by c-m on 2006-05-29
I have a 60gig FAT32 partition setup in ubuntu with all my windows stuff on there. everyone can read and execute form it, but only root has write access. 

I have tried to change this to 777 so everyone can read/write etc.. but for some reason it won't allow it. I just get an error in nautilus (as root) saying permissions could not be changed. 

here is the fstab line

/dev/hda2 /media/windows vfat rw,user,uid=carl,noauto,exec 0 0

can anyone help please?

---

### Post by Sutekh on 2006-05-29
[quote=c-m]I have a 60gig FAT32 partition setup in ubuntu with all my windows stuff on there. everyone can read and execute form it, but only root has write access. 

I have tried to change this to 777 so everyone can read/write etc.. but for some reason it won't allow it. I just get an error in nautilus (as root) saying permissions could not be changed. 

here is the fstab line

/dev/hda2 /media/windows vfat rw,user,uid=carl,noauto,exec 0 0

can anyone help please?[/quote]You cant change permissions in that way.  You need to specify the **umask** in the /etc/fstab

Unmount the partition```
sudo umount /media/windows
```Change the line to```

/dev/hda2 /media/windows vfat iocharset=utf8,umask=0000 0 0
```
Then mount the partition again
```
sudo mount /media/windows
```

---

### Post by c-m on 2006-05-29
[QUOTE=Sutekh]You cant change permissions in that way.  You need to specify the **umask** in the /etc/fstab

Unmount the partition```
sudo umount /media/windows
```Change the line to```

/dev/hda2 /media/windows vfat iocharset=utf8,umask=0000 0 0
```
Then mount the partition again
```
sudo mount /media/windows
```[/QUOTE]

I did try to unmount it before but apprently its mounted at /windows now and not /media/windows :???:    Could it be because i specified /windows in the partition wizard during installation?

carl@carl:~$ sudo umount /media/windows
Password:
umount: /media/windows: not mounted
carl@carl:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy
carl@carl:~$

---

### Post by Sutekh on 2006-05-29
[quote=c-m]I did try to unmount it before but apprently its mounted at /windows now and not /media/windows :???:    Could it be because i specified /windows in the partition wizard during installation?

carl@carl:~$ sudo umount /media/windows
Password:
umount: /media/windows: not mounted
carl@carl:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy
carl@carl:~$[/quote]Could be...

Lets find out where it is
```
sudo fdisk -l
```
will list your partitions
```
cat /etc/fstab
```
so I can see your whole fstab

---

### Post by c-m on 2006-05-29
carl@carl:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          65      491368+  82  Linux swap / Solaris
/dev/hda2            1396       10340    67624168+   b  W95 FAT32
/dev/hda3   *          66         879     6153840   83  Linux
/dev/hda4             880        1395     3900960   83  Linux

Partition table entries are not in disk order
carl@carl:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               reiserfs notail          0       1
/dev/hda4       /home           reiserfs defaults        0       2
/dev/hda2       /windows        vfat    defaults        0       0
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

#/dev/hda2     /media/windows    vfat     utf8,users,rw,uid=yourusername     0     0
/dev/hda2 /media/windows vfat rw,user,uid=carl,noauto,exec 0 0
carl@carl:~$

---

### Post by Sutekh on 2006-05-29
[quote=c-m]
/dev/hda2       /windows        vfat    defaults        0       0

#/dev/hda2     /media/windows    vfat     utf8,users,rw,uid=yourusername     0     0
/dev/hda2 /media/windows vfat rw,user,uid=carl,noauto,exec 0 0
[/quote] Not a good idea to have two different mount entries for the same partition.

You should unmount the partition
```
sudo umount /dev/hda2
``` Then comment out the hda2 lines and leave just this one
```

/dev/hda2 /media/windows vfat iocharset=utf8,umask=0000 0 0
``` Then try to mount it again.
```
sudo mount /dev/hda2
```
If that works then feel free to add other options, the options I use generally work all the time.

---

### Post by c-m on 2006-05-29
lol didn't notice it was in there twice, must have been done on installation.

works much better now, thanks for all the help.

---

### Post by Sutekh on 2006-05-29
Kewl no problem!

---

