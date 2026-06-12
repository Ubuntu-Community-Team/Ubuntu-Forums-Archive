---
title: "Wine crash and locking xserver on 11.04"
date: 2011-07-10
forum: General Help
---

### Post by fox_cream on 2011-07-10
Hi, 

Recently upgraded to 11.04 - everything was working well in 10.04.  However, running programs in wine (or running wincfg) now causes the xserver to lockout after a random interval.  At best, I get dumped back to the gdm, at worst it needs a hard reboot.   I've tried using wine versions 1.3 and 1.2, but both cause the same problem.  I've also tried installing ldfontconfig from 10.04 as I read that this was a resolution for people  having similar issues, but no joy. 

I'm running 64 bit ubuntu, and have an ati graphics card 

Anybody had similar problems, or got any thoughts?  This is a real deal breaker for me - I need MSOffice, but really don't want to go through the hassle of downgrading to 10.04.  

Cheers,

---

### Post by dino99 on 2011-07-10
64 bits is your choice :)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

wonder if your grahic driver is activated.

note: for wine issue post on the dedicated subforum, not here.

---

### Post by matuskap on 2011-07-10
I doubt its caused by the fact that youre using 64 bit version. I use 32 and have the very same problem. It all started when i updated wine (accidentally) with other updates. Applications that didnt have problems before started to freeze randomly. This problem seems to be very common novadays and most people say its caused by graphic drivers (99% of ppl having this problem have ATI graphic cards, im one of them). All I know is that its probably not caused by compiz or sound driver issue (like some teories suggest) cause i spent 2 days disabling, removing and reconfiguring with no difference at all. Anyway, not even returning to previous version of wine helped, just like i didnt help u right now, just wanted to let u know ur not alone :D

---

### Post by fox_cream on 2011-07-10
> **dino99 said:**
> 64 bits is your choice :)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)



The issue is nothing to do with 64bit - 've been using it since 9.04 and not had any issues (wine or otherwise) prior to updating to Natty.  64bit is a good choice to activate more than 4gb of ram instead of messing around with a PAE kernel.  

> **matuskap said:**
> Anyway, not even returning to previous version of wine helped, just like i didnt help u right now, just wanted to let u know ur not alone


Thanks for non-helpful solidarity - :P . I'm with you though - it probably is an ATI driver issue. Any idea how to debug (i.e. which logs), because I can easily replicate a crash??!  Thanks,

---

### Post by matuskap on 2011-07-10
> Thanks for non-helpful solidarity - :P . I'm with you though - it probably is an ATI driver issue. Any idea how to debug (i.e. which logs), because I can easily replicate a crash??!  Thanks,

Since Rhythmbox, vlc and all non-wine related programs keep running without problem(even tho they cant be controlled anymore) i guess connecting to "freezed" pc via ssh should give you full access. I didnt try it yet, if ull then GL :).

---

