---
title: "Nautilus CD-DVD Burning problem"
date: 2006-01-26
forum: General Help
---

### Post by niccolo.canestrari on 2006-01-26
I try to use Nautilus for burning CD/DVD and all works right, but when I look for the contents of CD/DVD it's empty. Also the burning process take a long time compared with Nero burning rom in windows XP. here's my fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/dvdrw   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrw   udf,iso9660 user,noauto     0       0
/dev/hdh        /media/dvd   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

where:
hdc -----> LG CD/DVD RW
hdd -----> LG CD RW 

My kernel is 2.6.12
please help me tell what I've to do.

---

### Post by Icefox on 2006-01-26
Try GnomBaker

---

### Post by steve.horsley on 2006-01-26
Nautilus has never burned anyting but coasters for me. As IceFix said, try GnomeBaker. 

If that doesn't work either, t'll install a lot of KDE stuff in the process, but I suggest that you install and try k3b. It is the one that has been most reliable for me. It also has the greatest number of options that I don't understand, but the defaults are just fine.

---

### Post by BathroomNinja on 2006-01-26
Second for K3b.  Even though I use Gnome, K3b is the bomb-diggidy.

---

### Post by StefanoCole on 2006-01-27
For GnomeBaker I suggest you to install the gnomebaker_0.5.0-3 version. You can find it in Dapper repos (Universe). The version present in Breezy repos(gnomebaker_0.4.2-1) didn't work for me.

Stefano

---

