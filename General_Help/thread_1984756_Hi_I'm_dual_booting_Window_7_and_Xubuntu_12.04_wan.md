---
title: "Hi I'm dual booting Window 7 and Xubuntu 12.04 want to add more space to my linux os"
date: 2012-05-22
forum: General Help
---

### Post by jcer93705 on 2012-05-22
Hello guys I want to add more space to my linux partition since I'm loving XUBUNTU. So am I able to shrink my Window partition then resize the partition for my XUBUNTU for more space? I know I'm able to do that when i was dual booting different Windows. How Linux? Thanks.

---

### Post by ksprasad on 2012-05-22
Hi, 
 
Yes you can resize your XUBUNTU partition. boot with a gparted live cd and do the resize.
But i strongly suggest you first backup all your data since it is a risky process.
 
Regards,
ksprasad

---

### Post by cortman on 2012-05-22
DON'T shrink that Windows partition with GParted. Boot to Windows instead and shrink it there, using the Disk Management tool in Control Panel. Windows is very picky about its partitions and resizing from Ubuntu could very well break it.
Then expand your Ubuntu partition to eat up the fresh unallocated space, using the live CD and GParted.

---

### Post by Jose Catre-Vandis on 2012-05-23
> **cortman said:**
> don't shrink that windows partition with gparted. Boot to windows instead and shrink it there, using the disk management tool in control panel. Windows is very picky about its partitions and resizing from ubuntu could very well break it.
Then expand your ubuntu partition to eat up the fresh unallocated space, using the live cd and gparted.

+ 1  !!

---

### Post by oldfred on 2012-05-23
If you want some specific suggestions, post a screenshot from gparted.

---

