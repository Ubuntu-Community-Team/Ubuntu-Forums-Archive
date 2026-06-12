---
title: "sporadic booting problem"
date: 2010-07-20
forum: General Help
---

### Post by hollowhead on 2010-07-20
Sporadically my daughter's and my laptop are not booting. Both are Toshiba satellite laptops, newish different models, mine is an l350-262. I know you are going to ask for a system log file, but nothing appears. This is logical since the kernel is not unpacking itself. Sometimes you get a blank screen and no more (after the bios screen has disappeared), sometimes the ubuntu logo appears and the countdown reaches the 5th spot. Either way nothing more happens however much you leave it. Pressing the power button to switch it off then on again usually overcomes the problem although sometimes it takes 3/4 goes. Most of the time boot goes fine although it has got slower since the os was installed. Running lucid

uname -r
2.6.32-23-generic

on both systems, when both were installed this problem did not occur this suggests an upgrade over the last month has broken the system.

[https://bugs.launchpad.net/ubuntu/+bug/607802](https://bugs.launchpad.net/ubuntu/+bug/607802)

I've filed the above as a bug, when it first happened I thought it was a hardware problem but when it started on my daughter's laptop too I assume it is a software problem.  Anyone else had this?

---

### Post by terryt57 on 2010-07-20
Yes I'm seeing the same thing on a home built system. Asus motherboard with an i5-750 cpu. Hitting reset seems to work and I've never seen it hang twice in a row. It does seem to happen more often after entering the BIOS setup but I haven't tracked this closely.

---

### Post by hollowhead on 2010-07-21
Nice to know I'm not alone or going mad.....

---

