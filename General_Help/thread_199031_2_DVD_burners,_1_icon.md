---
title: "2 DVD burners, 1 icon"
date: 2006-06-18
forum: General Help
---

### Post by deb2006 on 2006-06-18
I have two DVD burners in my PC:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               xfs     defaults        0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/sdb1       /home           xfs     defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

I had to add the 2nd entry (dev/hdb) manually since the 2nd burner was not recognized automatically in 6.0.6 LTS. This _never_ happened in the Flights that were released before. Under "Places/Computer" I only have one icon for a DVD burner. However, the 2nd one works and is also mounted at this single icon. Huh? Is there any way to change this behaviour?

---

