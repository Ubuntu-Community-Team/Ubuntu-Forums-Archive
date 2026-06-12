---
title: "A Couple Minor Problems After Upgrading To 10.04"
date: 2010-05-10
forum: General Help
---

### Post by ALF102 on 2010-05-10
Hi, I have just upgrade my Ubuntu 9.10 Karmic Koala to 10.04 Lucid Lynx. Everything works perfectly fine. Though there are 2 minor problems that isn't that much lethal to my system.

 After two restart, I noticed that I don't see the part on startup where there's a word "Ubuntu"....you know, with the 5 dots underneath that words. Instead, there are a few text written there, but its too fast so I couldn't catch what it was written there.

Here is a specs of my system (in case it got anything to do with this):
eMachines
Intel Celeron(R) CPU 900 @ 2.20GHz
1.9GiB RAM
--------------------------------------------------------------------------------------------------------
 Oh and one more thing, I want to increase my partition size of Ubuntu by taking some of the free space I had on my other OS (Windows XP) and I want to confirm whether I can do it with my Ubuntu 9.10 LiveCD or do I have to burn a Ubuntu 10.04 LiveCD?

---

### Post by nikhilbhardwaj on 2010-05-10
> **ALF102 said:**
>  I want to increase my partition size of Ubuntu by taking some of the free space I had on my other OS (Windows XP) and I want to confirm whether I can do it with my Ubuntu 9.10 LiveCD or do I have to burn a Ubuntu 10.04 LiveCD?
the ubuntu 9.10 cd would do just fine
however resizing the primary partition where the os is installed can be trick buisness so proceed with caution.

---

### Post by ajgreeny on 2010-05-10
That is all part of the plymouth startup that does not work on a lot of machines.  One of mine will show it for a second and then it goes into a jumbled mess of high resolution, far over to the right, with just the letters **u** and **b** of ubuntu showing at the screen edge.  My old Acer Travelmate 2200 laptop did show it, but I took lucid off that as it ran far too hot (an ati graphics/power management problem, apparently).  My wife's new netbook with UNE 10.04 runs brilliantly, but does not show the splash? screen at all at startup and for only about 2 seconds when shutting down.

Many people are suggesting that plymouth is still very much an ongoing development application, and that it will get better.  I do hope so, as it looks a bit unprofessional on my main machine at least where I get that high resolution image scrambled to the right.

---

### Post by ALF102 on 2010-05-10
Ah, so its called Plymouth -_- Well, I think that future updates should fix that.

And also thanks, but now that you've mention to "proceed with caution" I think Wouldn't want to take any risk.

---

