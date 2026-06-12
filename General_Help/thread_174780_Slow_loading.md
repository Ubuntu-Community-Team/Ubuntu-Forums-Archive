---
title: "Slow loading"
date: 2006-05-12
forum: General Help
---

### Post by Zdravko on 2006-05-12
My Ubuntu 5.10 loads very slowly. The initial dark brown screen appears, stating "Loading modules". Then the black console appears, dumbing all the checks with [OK] at the end of the line. I noticed that more than 3-4 minutes it says: "Loading Linux image" and "Mounting devices" or something. Then I get an error message for 2 USB devices - bad file descriptor. Is it possible that the USB devices are causing the slow startup? And how can I remove them from loading part? Of course, later I would like to use them.

---

### Post by Zdravko on 2006-05-12
I will appreciate every help. :)

---

### Post by ZylGadis on 2006-05-12
A description of your system would really help diagnosing the problem. Do you use some weird file system, for example? Or even worse - a windows one?

---

### Post by Zdravko on 2006-05-12
I am currently using Ubuntu 5.10 with dual-booting WinXp.
There are 2 NTFS partitions. The rest - for Ubuntu.
I don't think there is something specific for my system. Only that it is a little old (3 years or so). I have the strong feeling that at least one of the USB ports does'nt work.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde8       /home           ext3    defaults        0       2
/dev/hde1 /media/hde1 ntfs user,fmask=0000,dmask=0000 0 0
/dev/hde5 /media/hde5 ntfs user,fmask=0000,dmask=0000 0 0
/dev/hde6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


---

