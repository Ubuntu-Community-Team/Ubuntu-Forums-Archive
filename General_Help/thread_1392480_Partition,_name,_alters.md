---
title: "Partition, name, alters"
date: 2010-01-28
forum: General Help
---

### Post by FlemmingJ on 2010-01-28
hi

It seems like my partitions change names(e.g. /dev/sdc1/) for no reason. And therfore wont mount. Ofcourse there is a reason, I know, but I can't find it. Mayby it has to with the boot sequence, i.e. in which line the disks are detected?
Any comments most welcome. Thanks.

my fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#UUID=3ca363d6-e79d-40cd-b048-55b29a89a9a3 /               ntfs    defaults,errors=remount-ro 0       1
UUID=8838f9f8-9e4e-3e81-b6b4-b2237694aa99 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/sdc1/ /media/reiserfs reiserfs defaults,notail,noatime 0 0
/dev/sdb1/ /media/fat32 vfat defaults,umask=0000,noatime   0 0
#/dev/sdd1/ /media/backup_USB	ext3	defaults,noatime,commit=60 0	0
/dev/sdd1/ /media/backup_ext3	ext3	defaults,noatime,commit=60 0	0


regards Flemming

---

### Post by sisco311 on 2010-01-28
Use the UUID to mount the partitions: [uhelp]community/UsingUUID[/uhelp]

---

### Post by garvinrick4 on 2010-01-28
Label partitions, right click on partition in gparted. Use media/what ever you label

Mine is like  sudo mount /dev/sda5 /media/lucid  (space after sda5)

Of course first make a directory:  sudo mkdir /media/lucid

Get to root:   chroot /media/lucid

get wifi access:   sudo cp /etc/resolv.conf edit/etc/

---

