---
title: "64 bit app on 32 bit Ubuntu"
date: 2011-02-25
forum: General Help
---

### Post by skthetwo on 2011-02-25
Just built an AMD x4 with 8Gb memory machine; I need the extra memory ( and maybe all the way to 16 Gb ) for a specific app ( Velvet, a genome assembly program ). 

In the long run of course I'll move to 64-bit Ubuntu but tactically, at the moment I wonder:

If I compile etc with the right 64 bit libraries, can I run the 64bit-Velvet app on 32-bit Ubuntu, and expect it to use long words to address and use all the memory that's there ?

---

### Post by seawolf167 on 2011-02-25
Short answer: No

64bit specific applications will not work on a 32bit install.

Futhermore, if you are running a 32bit OS, you will not see anything beyond 4GB of RAM (though with system reserved, etc. your actual amount could be between 3 - 3.5 GB)

---

### Post by Yellow Pasque on 2011-02-25
Just move to 64-bit ASAP. It should be fairly easy if you have a separate /home partition. If not, the longer you wait, the harder it will become to reinstall because of the pain of losing your customizations.

One other short-term solution is using PAE, though a single app will still be limited to 32-bit addressing: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by Slim Odds on 2011-02-25
You can waste a lot of time trying to do the impossible, or you can just use the 64-bit OS.

I've used it for a long time and it works just great.

---

### Post by skthetwo on 2011-02-26
So the consensus is bite the bullet it seems. OK - good news for me, I checked my other 3 self-built PCs - built over 5 years -  they all have the magic word 64 or Opteron in the description of the CPUs - so I can perhaps upgrade the whole cluster to 64bit.

And I shdn't be that hassled migrating - I remember the days of the conversion from 16 bit PDP-11s to 32 bit Vax.

And in those days when 16Mb ( yeah that's M not G ) was a lot of memory, we thought that an address  space of 4 Gb ( 2**32 == 4Gb, since 2**10 = 1000 then 2**30 = 1Gb etc )  was vassssst - in fact the operating system( VMS) reserved 2Gb address space for itself - the authors figuring, I guess, that 2Gb for apps was sufficient. 

We've hit that limit, in commodity, home computing at that in what, 25 years ? 

Thanks also for the PAE suggestion. Evaluating the specs right now. Ahh, yeah PAE - I remember later model PDP-11s and the virtual address space extension to 18 bits and the 4K memory paging shenanigans one did.

Thx.

---

