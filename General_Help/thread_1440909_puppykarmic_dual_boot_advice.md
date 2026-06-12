---
title: "puppy/karmic dual boot advice"
date: 2010-03-28
forum: General Help
---

### Post by lemmy999 on 2010-03-28
I would like to dual boot Karmic with Puppy Linux. I have had real problems with Grub 2 in the past and fear that I may get similar problems if i crack on with this idea.

Questions
1. Is there anything i should do prior to installing puppy in terms of backing up grub ( for instance)

2./home is on a separate partition. Can I point Puppy at that partition?

Anything I haven't thought of?

---

### Post by oldfred on 2010-03-28
I am not sure how puppy installs to the hard drive. If it gives you a choice on where to install its boot loader do not let it install it. Grub2 will find it. If it does overwrite the MBR just reinstall grub2 like everyone has to do after a windows install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Generally it is not recommended to share /home. Different distributions may have different versions of programs or settings that may conflict. You can use a different userid but that defeats the purpose of sharing. You can share data. I moved all my data from /home into a data partition and share that. Since I was using similar  Ubuntu versions I did copy most of my /home settings over, but only reuse on an upgrade/new install where the same programs may update settings.

You can directly mount a data partition or link to the folder in it.
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

