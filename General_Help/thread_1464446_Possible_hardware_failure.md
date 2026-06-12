---
title: "Possible hardware failure?"
date: 2010-04-28
forum: General Help
---

### Post by JohnFH on 2010-04-28
I'm at a loss in trying to debug a problem I have with my media centre.  Basically I'm getting random system hangs and when I say hang I mean proper hang - processor stops dead.  No animation, not network connectivity, no keyboard/mouse response, nothing.  As for it being random - it has happened during movie playback, during idle, after being up a short time, or a long time, it doesn't matter, so it can happen any time really.  The logs show nothing suspect, except they just stop and there is nothing common between the logs of two failures.  It happens on both my 'old' ubuntu 9.04 partition and on my new 10.04 partition.

If you have any ideas of what could be happening or how to go about tracking down the problem I would really appreciate it.  I'm well and truly puzzled.  

Thanks.

---

### Post by dino99 on 2010-04-28
so nothing into /var/crash ?

at first glance i'm thinking about fans problems and too high temperatures: could you check this point and install the applet monitoring cpu gdu temp and fans speed.

---

### Post by KrisWillis on 2010-04-28
It might be worth running memtest86 for a few hours to check if your RAM has developed any faults.

---

### Post by JohnFH on 2010-04-29
Thanks for the suggestions.  I had a look under /var/crash and there's absolutely nothing there, and I also ran a full memtest86 run with no failures (took nearly two hours).

Any other ideas?

---

### Post by Wiebelhaus on 2010-04-29
Download and run diagnostics on [UBCD]("http://www.ultimatebootcd.com/") , Cheers!

---

### Post by todak on 2010-04-29
From your description, it would appear you have an overheating issue. A good cleaning between the fins of the processor heat-sink (in addition to the usual other places dust accumulates inside your box) should take care of the problem. If you remove the fan/heat-sink assembly to clean it, remember to apply thermal paste between the processor and heat-sink.

---

