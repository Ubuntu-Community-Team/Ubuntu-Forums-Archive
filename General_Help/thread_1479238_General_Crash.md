---
title: "General Crash"
date: 2010-05-10
forum: General Help
---

### Post by Rockmon on 2010-05-10
My Ubuntu crashed and now it doesnt turn on. Hope u can stay reading all the problems.
First of all, I installed ubuntu 9.10 like a month ago, i dunno why, when it got the first time updated, in the boot menu there were two ubuntus and two recovery system of ubuntu. I didnt know why it had happen but i didnt care. All was really good ultil i updated to 10.04.

The first think was that the link of the boot menu that was the first one of ubuntu, when it got started, there was just a black window. I couldnt do nothing, and the recovery system also at first it was like if it would run but no. Then i started usig the second pair of buuntu links in the boot system.

It kept running pretty well since today. When I arrived home, i started to look at programs in the website of Slice of Linux and started to install many of them. Sudentlly, it went to the black window and i couldnt do nothing so I restarted the computer and in the recovery sstem i did the "repairing" of the broken programs, and it looked like it started again to run well. Then it log off and i couldn't go in again, cause everytime that i log in, immediatly appeared the logging place.

Finally, i dunno what happened but now, i can start the loging menu for few seconds, then it coms the black window. I dont know what to do, i got really desperate trying al things i though off. I also tough that the ubuntu cd could be used to reapir it as in windows but no. Help me please!

I was really pleased of ubuntu, but at the time it had all kind of problems :(((

---

### Post by cbecker78 on 2010-05-11
> **Rockmon said:**
> My Ubuntu crashed and now it doesnt turn on. Hope u can stay reading all the problems.
First of all, I installed ubuntu 9.10 like a month ago, i dunno why, when it got the first time updated, in the boot menu there were two ubuntus and two recovery system of ubuntu. I didnt know why it had happen but i didnt care.

That's because the update added a new kernel...  The second option was the old Kernel and could have been removed.




> The first think was that the link of the boot menu that was the first one of ubuntu, when it got started, there was just a black window. I couldnt do nothing, and the recovery system also at first it was like if it would run but no.If by the "first link" you mean the one that is at the top of grub with the newest version number, then your problem is that your upgrade did not install completely for some reason.

>  Then i started usig the second pair of buuntu links in the boot system.
So you began using the kernel integrated with 9.1 after trying the 10.04 upgrade... it's a small wonder it worked at all.  Much less for a few days.

Your only option at this point is to put in a live cd, mount your ubuntu partition, back up all of your data, then do a fresh install of either 9.1 or 10.04.  -Sorry that's the news I had to give you...

---

