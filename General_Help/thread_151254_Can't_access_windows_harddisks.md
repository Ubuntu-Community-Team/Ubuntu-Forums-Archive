---
title: "Can't access windows harddisks"
date: 2006-03-27
forum: General Help
---

### Post by Anessen on 2006-03-27
Hello
I am having problems accessing my old windows partitions, I am the only user on this install.
When I try to access my harddisks (for example, hdd1), I recieve the error message:
> Folder contents could not be displayed.
You do not have the permissions necessary to view the contents of hdd1.
This is an IDE harddisk, in fact it is the same one that Ubuntu is installed upon, so I can't see how the drive can be faulty. The partitions can be seen by other Linux installs, such as SuSE, Mandriva and Knoppix.

EDIT
I have just found out that I can access the drive if I go to System -> Administrations -> Disks, select the drive/partition and click the Browse button. It shows thumbnails for images etc fine. I can't access anything normally though...

---

### Post by aysiu on 2006-03-27
Maybe this will help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Anessen on 2006-03-27
Excellent, this worked perfectly! Thank you!

---

### Post by DOtSlaSHuCantCME on 2006-03-27
[QUOTE=Anessen]Hello
I am having problems accessing my old windows partitions, I am the only user on this install.
When I try to access my harddisks (for example, hdd1), I recieve the error message:

This is an IDE harddisk, in fact it is the same one that Ubuntu is installed upon, so I can't see how the drive can be faulty. The partitions can be seen by other Linux installs, such as SuSE, Mandriva and Knoppix.

EDIT
I have just found out that I can access the drive if I go to System -> Administrations -> Disks, select the drive/partition and click the Browse button. It shows thumbnails for images etc fine. I can't access anything normally though...[/QUOTE]


Dont know if you  know about your fstab,its located at /etc/fstab
in that file you will be mounting your drives,Now if the harddrive is "NTFS" then
you "might" have issues,reading ntfs partitions is still a work in progress for linux,ubuntu can read fat32 filesystems with no hassle,so maybe having a 5gig partition  (ntfs) for windows and the rest of space you can make like 2 fat32 partitions and move your data,mp3,movies to the fat32.

this link will help with understanding your fstab file [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

This is a copy of my fstab ,notice i just commented out my windows swap and xp partition so they dont show up as  drives on my Ububtu desktop,when you underdstand your fstab good enough to edit it, use                  "iocharset=utf8,umask=0000"(under option)(refer to my fstab) this will give you full read, write access to your fat32 partitions.
==================================================================


"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext2    defaults        0       0
#/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     vfat     iocharset=utf8,umask=0000       0       0
/dev/hda6       /media/hda9     vfat     iocharset=utf8,umask=0000      0       0
/dev/hda7       /media/hda6     vfat     iocharset=utf8,umask=0000       0       0
#/dev/hda8       /media/hda7     vfat    defaults        0       0
/dev/hda9       /media/hda8     vfat     iocharset=utf8,umask=0000       0       0
/dev/hdb2       /usr            ext2    defaults        0       0
/dev/hdb4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
==================================================================

---

### Post by kitovras on 2007-11-17
hello,
i can't see my windows drives either, but it seems to be due to an update i did to kernel... So i'm looking for a solution ... my fstab (  doesn't  look like yours at all, it has "sda" where you have "sda" may the problem be due to this change ? Shouldi remount these disks ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7d0bdfc0-8dbc-413b-9d9b-ecde8551c989 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=b9ba9128-9ace-4db8-aab3-8cdce1529406 /home           ext3    defaults        0       2
# /dev/sda1
UUID=80E9-C15B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=B660ECF460ECBC6D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=FE90F0A990F06A13 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=89b39acc-0cc5-4565-893d-1e78616c3b0e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-11-17
> **kitovras said:**
> hello,
i can't see my windows drives either, but it seems to be due to an update i did to kernel... So i'm looking for a solution ... my fstab (  doesn't  look like yours at all, it has "sda" where you have "sda" may the problem be due to this change ? Shouldi remount these disks ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7d0bdfc0-8dbc-413b-9d9b-ecde8551c989 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=b9ba9128-9ace-4db8-aab3-8cdce1529406 /home           ext3    defaults        0       2
# /dev/sda1
UUID=80E9-C15B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=B660ECF460ECBC6D /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=FE90F0A990F06A13 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=89b39acc-0cc5-4565-893d-1e78616c3b0e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by kitovras on 2007-11-18
[I]$ sudo fdisk -l


Disque /dev/sda: 160.0 Go, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf98d6e74

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         893     7168000   1c  Hidden W95 FAT32 (LBA)
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2   *         893       10622    78144512    7  HPFS/NTFS
La partition 2 ne se termine pas sur une frontière de cylindre.
/dev/sda3           10622       19457    70973793    f  W95 Etendu (LBA)
/dev/sda5           10622       14996    35135488    7  HPFS/NTFS
/dev/sda6           14997       16211     9759456   83  Linux
/dev/sda7           16212       16393     1461883+  82  Linux swap / Solaris
/dev/sda8           16394       19457    24611548+  83  Linux[/I]


so the disks corresponding to my two windows partitions are the two NTFS : sda2 and sda5. And these are supposed to be mounted in /media, at least that's what i've understood from other posts. i see them in that directory : 
[I]$ ls -l /media
total 14
lrwxrwxrwx 1 root       root          6 2007-11-12 21:14 cdrom -> cdrom0
dr-xr-xr-x 3 4294967295 4294967295   88 1998-11-15 03:28 cdrom0
drwxrwx--- 6 root       plugdev    4096 1970-01-01 01:00 sda1
drwxr-xr-x 2 root       root       4096 2007-11-12 2 1:14 sda2
drwxr-xr-x 2 root       root       4096 2007-11-12 21:14 sda5
[/I]

but ls -la tells me they are empty ( i can see the all the files contained in my windows recovery partition sda1 though !) . Do you know what is happening ? Is it due to a problem in one of the recent updates ? )

Kitovras

---

### Post by kitovras on 2007-11-25
i finally found the problem :D the thing is that windows partition are unavailable if windows is put to hobernation instead of being closed but everything works all right otherwise ;)

---

