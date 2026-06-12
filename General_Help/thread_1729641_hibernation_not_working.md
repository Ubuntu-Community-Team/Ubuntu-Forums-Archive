---
title: "hibernation not working"
date: 2011-04-15
forum: General Help
---

### Post by matteosistisette on 2011-04-15
Hi,

Hibernation on my laptop doesn't work.

When I try to hibernate (either manually or automatically because battery goes critically low), any of the following can happen (randomly):

A. During the hibernation process it hangs forever with a black screen (with or without some error messages unanderstandable to me) and never terminates hibernation. I have to manually turn it off by holding the power button, and when I turn it on again, it does a fresh boot.
B. Instead of hibernating, it just locks screen. 
C. It (apparently) terminates the hibernation (the power goes off automatically as if it had succesfully hibernated, even if AC power is connected), but then, when I turn the computer on, instead of resuming it does a fresh boot.
D. It hibernates succesfully and when I turn it on it resumes succesfully. This almost never happens; it has been a long long time since the last time it happened.


I am far from being the only one and this has been so for years. The bug has been reported in launchpad by a lot of people a long time ago, so if it has not been fixed in such a long time it must mean that the developers don't think it deserves much attention. (Which is strange by the way, because an operating system with non-bulletproof hibernate/suspend is an operating system that you just cannot safely use, at least on a laptop.)

Does anybody know of some workaround? Is there a way to find out what is causing the hibernation to fail so that I may try to find a manual fix?

thanks
m.

---

### Post by Hippytaff on 2011-04-15
How much space do you have a loocated for the swap partition?

---

### Post by matteosistisette on 2011-04-15
> **hippytaff said:**
> how much space do you have a loocated for the swap partition?

2.2 gb

---

### Post by Mark Phelps on 2011-04-15
My guess is the reason that hibernation problem have not been fixed is that they are specific to every single PC.

Wierd combinations of drivers (even different versions of the same driver) and hardware can prevent hibernation.

Even in the MS Windows world, where drivers and hardware tend to be better supported, hibernation is a hit or miss proposition.

---

