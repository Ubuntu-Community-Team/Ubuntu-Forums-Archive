---
title: "How to modify fstab to make my account be able to write on FAT32 partitions?"
date: 2006-03-13
forum: General Help
---

### Post by Dislimit on 2006-03-13
How to modify fstab to make my account be able to write on FAT32 partitions?

I have modified /etc/fstab to make my FAT32 partitions accessable when booting up. But now only root can write to it. Is there any way to make my account (in admin group) be able to write to those partitions directly? (not sudo su)

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       
1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda3       /mnt/d          vfat    
defaults,codepage=936,iocharset=utf8 0 0
/dev/hda5       /mnt/e          vfat    
defaults,codepage=936,iocharset=utf8 0 0

---

### Post by Sutekh on 2006-03-13
[QUOTE=Dislimit]
/dev/hda3       /mnt/d          vfat    
defaults,codepage=936,iocharset=utf8 0 0
/dev/hda5       /mnt/e          vfat    
defaults,codepage=936,iocharset=utf8 0 0[/QUOTE]
Change these to
```
/dev/hda3  /mnt/d  vfat  codepage=936,iocharset=utf8,umask=0000  0  0
/dev/hda5  /mnt/e  vfat  codepage=936,iocharset=utf8,umask=0000  0  0
```
Out of curiousity, why codepage=936? (I thought I should leave that in)

---

### Post by frodon on 2006-03-13
Dislimit, don't forget the breezy starter guide, it contains many useful infos like the one you need here : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

