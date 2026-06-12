---
title: "FStab, for write suppport?"
date: 2006-05-13
forum: General Help
---

### Post by Dakaru on 2006-05-13
Ok here is my Fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1	/mnt/secondary	ext3	defaults,user,exec	0	0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1	/mnt/media	ext3	defaults,user,exec	0



I want to be able to write to the hdd1 partition, but for some reason I can't, any ideas?

---

### Post by aysiu on 2006-05-13
Have you tried this? ```
sudo chown -R Dakaru:Dakaru /mnt/media
```

---

### Post by Dakaru on 2006-05-13
[QUOTE=aysiu]Have you tried this? ```
sudo chown -R Dakaru:Dakaru /mnt/media
```[/QUOTE]
That did it :D Thanks.

---

