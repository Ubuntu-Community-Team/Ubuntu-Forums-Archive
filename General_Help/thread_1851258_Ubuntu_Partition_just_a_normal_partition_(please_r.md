---
title: "Ubuntu Partition just a normal partition? (please read explanation)"
date: 2011-09-27
forum: General Help
---

### Post by Waff1es on 2011-09-27
Hey guys,

After a failed attempt at jumping over to Ubuntu (video driver compatibility support issue), I have had half of my hard drive being wasted with the unused Ubuntu install. My computer was a pure Win7 partition until I opted into that Ubuntu 11 setup option where it splits an existing partition into two partitions for dual booting. It sounded experimental but so far I've encountered no issues. 

I now got my hands on the Windows 8 dev build and I want to install it on the existing Ubuntu partition. Is the partition anything special other than being derived from another partition, or can I treat it like any other partition and slap Win 8 on it?

Any input would be great.

---

### Post by wildmanne39 on 2011-09-27
Hi, being windows you may have to boot with the livecd and unmount the partition and make it an ntfs before you can install windows on it.
Thank you

---

### Post by dFlyer on 2011-09-27
I haven't used windows in many years, but my guess is that you would boot your windows 8 disk and select the partition that ubuntu was on and have windows over write it with NTFS or what ever they use.

---

### Post by Blasphemist on 2011-09-27
Normally an extended partition is created by the Ubuntu install and within it 2 logical partitions. One for Ubuntu and one small one for swap. I'd think it best to prepare for win 8 by deleting first the logical partitions and then the extended. This would leave you with un-allocated space that win 8 could use. I have no experience with win 8 but it ought to be able to recognize un-allocated space and use it without breaking win 7. 

I'd boot the Ubuntu live cd and run GParted to make this change.

---

### Post by Waff1es on 2011-09-27
Alright guys, I will definitely need to check out your suggestions.

Being a CS student it's almost seems sacrilegious installing Windows on top of Linux :P. I got a Studio XPS 1340 with hybrid video card(s) right now and it doesn't play nicely with Ubuntu unfortunately. Maybe next computer...

---

