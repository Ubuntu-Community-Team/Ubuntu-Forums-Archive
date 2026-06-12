---
title: "Screwed up my PC"
date: 2010-06-05
forum: General Help
---

### Post by Delsos on 2010-06-05
Ok so i installed Ubuntu as a partition on my laptop with windows XP. later i went to xp and disc management and deleted the ubuntu partition and that partition became unalocatted space. so i used a program to stretch the drive into 1 drive again. after a restart i am getting the grub> rescue no such partition. i am not too familiar with linux commands ... 
i tried taking the cd that i burned the ubuntu image and starting up with that, and it starts up, but then it goes to the screen where it shows ubuntu loading, and it just keeps on loading forever and the disc drive makes a weird ticking noise, and thats the end of that. i cant find my windows xp cd :(
 
please try to help me, we really need this computer to work.
 
thanks and sorry for my ignorance.

---

### Post by radddi on 2010-06-05
Hello, Delsos,

As far as I understand, you installed Ubuntu and then deleted its partition from a Windows program. The problem here is that the system still boots from Ubuntu's bootloader (GRUB) in stead of from the Windows one. Therefore it looks for the GRUB configuration in the Linux partition, which sadly doesn't exist.

I've experienced this issue and have used the Windows XP disk in order to recover the MBR (Master Boot Record):
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

But since you can't find your CD, you may want to try this alternative solution using the Ubuntu LiveCD and the Internet:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

.:CheerS:. and hope this helps. :guitar:

---

