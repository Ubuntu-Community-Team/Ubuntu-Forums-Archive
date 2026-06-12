---
title: "Problem in booting"
date: 2012-05-08
forum: General Help
---

### Post by sinaphysics on 2012-05-08
Today after installing ubuntu 12.04, My monitor distorded and its color destroyed and after restart the monitor is full of different incredible colors which I can't  access boot section. What do you suggest?

---

### Post by wilee-nilee on 2012-05-08
Are you even getting to the grub menu, if not hold down the shift key at the bios to see it and look at this link for inserting nomodeset in the kernel to boot in. Once in get fully updated and look in additional drivers for any offered. This is basically a one time low graphic boot, if needed every time it can be inserted in the kernel.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sinaphysics on 2012-05-09
I visit a computer supporting center and the repairer said me the problem is in graphic card!!!!
I should pay for repair. I don't know the 12.04 was responsible for this problem or the graphic card reachs to final countdown of life :(
you know the problem is that I can't see the setup section to do something about boot, I think this is just a hardware problem.
what do u think?
:/

---

### Post by wilee-nilee on 2012-05-09
> **sinaphysics said:**
> I visit a computer supporting center and the repairer said me the problem is in graphic card!!!!
I should pay for repair. I don't know the 12.04 was responsible for this problem or the graphic card reachs to final countdown of life :(

Some cards like nvidia and ati/radeon cards need a driver that may be in the repos.

Did you try the nomodeset option?

If that gets you in it just may be a matter of updating the OS and looking in the additional drivers app for a driver.

---

### Post by sinaphysics on 2012-05-09
No, I don't try the nomodeset, It's a bit hard for me. I'm not enough experienced in this kinda problems. but I remember I fall in this problem when I was in ubuntu 12.04 in additional driver section I was installing the driver file for graphic card.
what u think? can this be the main problem and my hardware is safe ??

---

### Post by wilee-nilee on 2012-05-09
> **sinaphysics said:**
> No, I don't try the nomodeset, It's a bit hard for me. I'm not enough experienced in this kinda problems. but I remember I fall in this problem when I was in ubuntu 12.04 in additional driver section I was installing the driver file for graphic card.
what u think? can this be the main problem and my hardware is safe ??

Probably, the tech you went to may or may not know linux hard to say I was not there. With windows setups you may not have had this problem so they may have assumed the card is broken? When what you need is a driver, so look at the nomodeset link and try that. The nomodeset option is to boot in, in a low graphics mode.

If you get in update the OS and then look in additional drivers you can find that in the dash the top button in the left panel if you are using unity.

I'm guessing here as to the techs opinion and whether your computer hardware is broken or not.

All I can do here is give you the standard tools to get in if possible and possibly get the graphic drivers needed.

---

