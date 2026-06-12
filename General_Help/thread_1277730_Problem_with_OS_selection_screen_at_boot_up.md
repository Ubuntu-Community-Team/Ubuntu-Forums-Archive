---
title: "Problem with OS selection screen at boot up"
date: 2009-09-28
forum: General Help
---

### Post by hxleet on 2009-09-28
Hello all let me start by saying im new to the forum.  I've looked and searched these forums for a while now and i finally registered to the best one i've found i've been able to trouble shoot alot of problems in Ubuntu 9.04 from these forums so i thought i would join.

On to the problem at hand(well not really a problem just buggin me really).  My ubuntu works fine the only issue im having is at boot up ( i dual boot ubuntu and WinXP- XP is for my wife she hates ubuntu)  i get to the OS selection screen and theres 4 lines for ubuntu and then my normal 1 for XP.  2 say generic kernel and 2 say somethin along the lines of safe mode ( mind drawing a blank ill edit it and say exactly what the lines are)  but basically its showing 2 ubuntu installs.  My question is why am i showing 2 installs of ubuntu I think it happend after i updated for the first time. i had ubuntu installed before and it was showing 4 instals for ubuntu so i formatted my WHOLE drive xp and all and went back with 2 clean installs of both OS's.  Now its showing only 2 been like this for a few months now before it had multiplied 4 times in about a week or 2. I can not for the life of me figure out why it's showing 2 installs.  I have never used any other linux distros before so not sure if this is normal or not.  Any advice on this issue would be greatly appreciated.

hxleet

---

### Post by Brian Vaughan on 2009-09-28
What you've described sounds normal.

Most likely, the two versions of Linux you're describing are actually both options to boot Ubuntu, one with the current version of the Linux kernel, the other with the previous version. After a short delay, GRUB will boot Ubuntu with the current version of the kernel, by default.

The previous version of the Linux kernel is present just in case it turns out you've got some trouble with the current version, such as some application not being compatible with it. It's just a precaution, and you'll probably never need to boot a previous version of the kernel. If you did choose to boot with the previous kernel, you probably wouldn't notice any difference, but you're usually best off just using the current version.

Occasionally, there will be more kernel updates, leading to a longer list of items in GRUB. New Ubuntu distributions will clean them out.

---

### Post by hxleet on 2009-09-28
Ahh i was losing my mind trying to figure this out but that actually does sound logical.
thanks for the reply Brian.  So far every thing works great. lovin me some ubuntu.

*Mod* close forum this pretty much sums it up.

---

