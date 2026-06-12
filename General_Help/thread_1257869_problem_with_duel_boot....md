---
title: "problem with duel boot..."
date: 2009-09-04
forum: General Help
---

### Post by sumeet_singh on 2009-09-04
Hey guys ...... firstly i would like to say I LOVE UBUNTU.... man it's gr8...
now coming to the topic... I had installed ubuntu woth windows xp in duel boot.. and everything was all gud... bt i made a mistake... i jst installed windows vista on another partition...so wat i got was three differen os on three diffrent partitions.....
now the problem is each time i boot.. i jst a boot screen tat's probably not grub.... with jst two options of windows xp and vista.... i jst want to know how do i get rid of windows vista from my machine.. and how to restore grub...
i tried formatting the drive on which windows vista was installed.... but after tat i still get the windows boot manager....with the same two options... plzz tell me how to remove this boot manager... nd get ubuntu to work...:confused:

---

### Post by denarced on 2009-09-06
Sounds like Vista took over the boot-sector and therefore destroyed grub.
Re-installing grub should fix the issue.

---

### Post by estebarb on 2009-09-06
Yes, it will we solved reinstalling GRUB, BUT beware: don't install it in the MBR, or the Windows are not going to be able to start.

---

### Post by Bucky Ball on 2009-09-06
Download, burn and boot from SuperGrubDisk. That will set up a grub to get all three booting if that is what you are after:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

---

### Post by lisati on 2009-09-06
<aside>I think you mean "du**a**l boot" (which will probably result in more useful results when searching). "Du**e**l boot" sounds like a piece of footwear you'd wear to a fight.</aside>

---

### Post by sumeet_singh on 2009-09-06
hey thnx dude's.... problem's solved...

---

