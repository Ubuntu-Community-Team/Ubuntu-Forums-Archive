---
title: "Cpu-z / cpu-g"
date: 2010-08-09
forum: General Help
---

### Post by jp351 on 2010-08-09
ok, i've been looking around and found out about this CPU-Z by CPUID.. well, go figure, it won't run on my system. it says somethign about needing an older driver, which is already running... or something. idk, it makes no sense, like contradicting itself within one sentence.. anyway, i found out about CPU-G which is supposed to be a good replacement.... well, what i'm looking for mainly is something like Z that tells me EVERYTHING it can know about my system that i don't know.. like my cpu fsb... no, i don't know it, but i'd like to so that i can get ram at that speed for optimal performance.. anyone have any suggestions???

thanks.. :)


*EDIT*
the only thing CPU-Z tells me is that i'm using windows xp pro, sp3, and directx 9.0c.

---

### Post by pbrane on 2010-08-09
You can type:
```

cat /proc/cpuinfo

```
in a terminal and get most of this info. If you know the type of CPU you have you can always look it up to see what speed the FSB is. FSB is not usually in the CPUID.

I found this too.
[http://www.majorgeeks.com/download.php?det=214]("http://www.majorgeeks.com/download.php?det=214")

---

### Post by jp351 on 2010-08-09
thanks for the info, but that's told me just the same info that CPU-G did. any suggestions on how i could find the fsb of my cpu??

thanks. :)

---

### Post by QLee on 2010-08-09
[QUOTE=jp351]
...
like my cpu fsb... no, i don't know it, but i'd like to so that i can get ram at that speed for optimal performance.. anyone have any suggestions???[/QUOTE]

Go to one of the memory suppliers' web pages (for example, Crucial.com) and use their application. You can enter the system you have and it will show you the compatible memory available for that system.

---

### Post by clhsharky on 2010-08-09
jp351

I know it might not help you, but I boot XP check cpuz and then I know.
Settings are in BIOs anyways.

Sharky

---

### Post by jp351 on 2010-08-09
i actually have the crucial.com info page on my MOBO bookmarked in firefox for easy reference. but at crucial they list all kinds of ram, from pc2-3200, all the way up to 8500, CL5, CL6, CL7... all ranging between 1.8 and 2V.. 4-4-4-12, 5-5-5-15.... which is all good to know.............. but i can't figure out the bus speed of my cpu. now, i know that amd cpu's are a little bit more perticular, but i am running an intel chip *sigh's and shrugs* but still, a 32-bit OS only addresses 3-3.5gb of ram, so with the gaming i'm going to be doing, along side all of the side apps that'll be running background, i'd like to have my cpu/ram running sync, as opposed to not, just for the best performance.

---

### Post by cascade9 on 2010-08-09
clhsharky has told you the easiest way, check in the BIOS. 

If your worried about going into the BIOS, then just post the exact CPU model and then somebody will tell you the FSB ;) 

Running faster memry than your FSB isnt normally an issue.....if the chipset cant handle the extra speed, it will just run at the normal speed. If you know what you are doing, and have RAM that is faster than your FSB (eg running DDR2 1066, but the FSB is limited to 667) then changing the CAS ratings can increase perfromance. 

32bit can use more than 3.5GB, using PAE.

---

### Post by clhsharky on 2010-08-09
jp351

> but i can't figure out the bus speed of my cpu
Go to CPU manufacture for that info.

Go to motherboard manufacture for recommended memory.

Even cpu-g tells you your CPU and Motherboard.

>  i'd like to have my cpu/ram running sync, as opposed to not, just for the best performance.
True for older AMDs but not Intel or newer AMD chips.

Sharky

---

### Post by QLee on 2010-08-09
jp351,

At the Crucial site, they have an application in which you enter what computer you have and they show you the sticks that are compatible with your system. No need to sort through and figure it out for yourself. No need to know anything but the make and model number of your computer and/or mainboard.  You can't choose better than their application.

---

