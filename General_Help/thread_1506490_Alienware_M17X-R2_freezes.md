---
title: "Alienware M17X-R2 freezes"
date: 2010-06-10
forum: General Help
---

### Post by DraeKlae on 2010-06-10
My new Alienware M17X-R2 notebook freezes when it's working on battery power and the AC adapter is then plugged in. If I do that while Ubuntu isn't running -- while the computer is booting, for instance --, then it doesn't freeze, so the problem must be with Ubuntu. By the way, I also experience freezing sometimes when booting, but that is linked with plymouth and fsck not wanting to coexist and, therefore, probably unrelated with the other issue.

---

### Post by drbcladd on 2010-07-29
(1) What version of the BIOS are you running? I had the same behavior using A03; don't upgrade to A04 if you can help it as that has made everything worse: the machine fails to charge when running and on AC, it fails to recognize the Dell charger as being powerful enough to run the system, some fraction of the time on boot it thinks it is not plugged in at all, and it always wants to turn on integrated graphics.

What kernel are you running? (2.6.32-24-server) Any difference when you fall back to earlier kernels?

(2) What graphics are you running? I hav nVidia 260M and am running the most current (256.35) proprietary drivers.

(3) I talked to Dell since there are problems at boot, before Linux gets to touch anything (there are also, obviously, problems in Linux, too) and they claimed that there will be a new BIOS release ("any time now") that addresses the power issues. 

(4) Do you have any problems with the system crapping out (corruption in low memory, paging fault, bios corruption) on boot? Combining a pain in booting with a sure crash if I unplug from power, this monster is not so portable as it once was.
I think (scientific wild-*** guess) the power problems in the BIOS are causing the problems in Linux64. 

Here's hoping they fix their stuff and we can get some useful debugging information for the

---

### Post by drbcladd on 2010-08-11
Ping. 

Meant to ask one more question: What video card/driver combination are you running? With more information I can limit where the problem lies.

Okay, two more: How many hard drives do you have installed? I am wondering if I am overtaxing the power supply in some way. 

It appears that the A05 version of the BIOS does NOT fix the problem. Doesn't make it worse (and fixes the boot crap with A04, at least so far).

---

### Post by Kmim on 2010-10-22
I had this problem also! I disabled Hybrid and my Nvidia card and only my integrated video is enabled, now I am able to unplug, replug, and no freezing. Hope this helps

---

