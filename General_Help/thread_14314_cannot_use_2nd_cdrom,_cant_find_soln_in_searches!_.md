---
title: "cannot use 2nd cdrom, cant find soln in searches! HELP!!!!!"
date: 2005-02-06
forum: General Help
---

### Post by Datchew on 2005-02-06
searched all over this site for the last hour and I've found a few questions like mine, but no answers. 

I have a dvd-rom that was present when i installed ubuntu and is working fine. 
I installed a cd-rw drive and cannot use it except when i run the k3b program. 

cannot see it when i browse the file system .
Here's my /etc/fstab file.  

**********************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**************************************************

Please help.  i'm sure this is something easy, but i'm rather new at this linux stuff.

---

### Post by Datchew on 2005-02-07
bump!

still waiting on any replies!  (patiently)

---

