---
title: "What to change in fstab to mount this harddrive..."
date: 2006-03-22
forum: General Help
---

### Post by jms830 on 2006-03-22
I just used gparted to convert an ntfs partion to reiserfs. it was/is hdb1

what do i change in my fstab and how do I mount it? below is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda3       /fat32        vfat    iocharset=utf8,umask=000        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dragonfyre13 on 2006-03-22
Take a look at this. It has some good information on Fstab in my wiki.

[http://www.dragonfyre13.com/TimWiki/MountFileSystems](http://www.dragonfyre13.com/TimWiki/MountFileSystems)

---

### Post by jms830 on 2006-03-22
that is helpful, but more so if i was going from reiserfs to ntfs...

however, I got rid of the ntfs and now want reiserfs...

any more help possibly?

---

### Post by jms830 on 2006-03-22
actually ok i think i got it right, how does this look?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb1       /media/hdb1     reiserfs notail           0       0
/dev/hda3       /fat32        vfat    iocharset=utf8,umask=000        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

