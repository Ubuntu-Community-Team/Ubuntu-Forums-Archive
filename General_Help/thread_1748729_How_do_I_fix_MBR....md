---
title: "How do I fix MBR...?"
date: 2011-05-03
forum: General Help
---

### Post by brianlen on 2011-05-03
I'm deleting Ubuntu because something is wrong when I reinstalled. I'm thinking when I delete the Ubuntu volumes, the data is actually still in there, so when I reinstall on those volumes it messes with the new install. I'm trying to actually delete the data on the volumes. When the volumes are "deleted" Grub no longer boots my systems, so how do I fix MBR without a Windows boot disk to boot back into Windows?

---

### Post by Hedgehog1 on 2011-05-03
You can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") recovery disks, and create a Windows recovery disk for your system.  You may need to make it on another PC if you have already deleted Ubuntu.

Once it is made: Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

***The Hedge***

:KS

---

### Post by hometow1 on 2011-05-03
c:\fdisk/mbr

---

