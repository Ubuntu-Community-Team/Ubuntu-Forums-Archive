---
title: "grub error 21"
date: 2010-09-04
forum: General Help
---

### Post by TylerTheWonderfull on 2010-09-04
Hello,

A few weeks ago I put another hard drive in my computer and installed ubuntu on it.. yesterday I got two more hard drives that are better than the other one and i want to replace the old one with them... but I've found a problem.. when i take out the hard drive with ubuntu on it my computer wont boot.. it just gives me "grub error 21"... how can i remove the old drive and avoid this??

-Tyler

---

### Post by ajgreeny on 2010-09-04
Your problem is that the files grub needs to boot properly are on your ubuntu root partition, so when you remove that disk, grub has no information to act on, and gives you that error message.  If you want to put ubuntu back again, just reinstall onto the new second disk and all should be OK again

I am assuming you have windows of some sort on your first disk,and do not want to reinstall ubuntu straight away.  If so, you need to restore the windows MBR boot loader to get back to booting windows using your windows CD, then remove the second disk and lastly, when ready, install ubuntu again on your newer, better second disk.  When you install this time, I suggest you put grub on the second disk, not on the first where it will replace the windows MBR again.

To do this, you need to click on the **Advanced** button in the final step of installation (7 or 8, I can't remember) and in the dropdown box choose sdb, not sdb1 or sdb2, just plain sdb.  Now when you boot you can set the BIOS to use either disk 1 or 2 as first device.  If you use 1 the system will boot straight to windows, if 2 you will get the grub menu and can choose which OS to boot to.

---

### Post by TylerTheWonderfull on 2010-09-05
Okay so I got ubuntu installed on my new drive... still getting the error.. 

And Yes my main drive has windows 7 on it.. I put the disk in to fix what you said but how do I do that? I had it do a "computer repair" and it searched for problems booting but couldn't find any.. do I have to reinstall everything?

---

### Post by ajgreeny on 2010-09-06
I'm sorry but I can't help with windows 7 as I have never used it.  My last windows was XP, which was easy to restore the MBR, but I know win7 is a lot different, but nothing more.

Google is your friend here, I think.

---

