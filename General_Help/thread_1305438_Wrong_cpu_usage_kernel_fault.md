---
title: "Wrong cpu usage: kernel fault?"
date: 2009-10-29
forum: General Help
---

### Post by psychok9 on 2009-10-29
Today i've discovered an problem with my **Karmic x86_64** updated Ubuntu, kernel 2.6.31-14-generic and Intel Quad Q6600 cpu.
gnome-system-monitor and also "top" from the terminal, show incorrect cpu usage (over 100%-> 200% etc), like don't display correctly an 4 cores balanced load.
When i show graphs, they display 4 cores correctly.

---

### Post by Giblet5 on 2009-10-29
Can you post screen shots?

I've got a Q6600 box next to this one and it looks correct.

I can start a 4-thread cpu-waster (loops at full speed, adding 0.00000001 to 0.0 over and over) and all four cores go to 100% and hold there.

I'm not saying that it isn't happening on your system: I just think screenshots will help identify the problem, because as you say that isn't normal.


Also note that there is very little to "balance" your core usage... Technically, there is nothing to balance core usage, but it kinda works out that way by accident. Or providence.

---

### Post by psychok9 on 2009-10-30
Very strange: I've discovered an option on gnome-system-monitor, Solaris mode, and this fix the problem balancing % on all cores.

Maybe it's a modify with Karmic version?
On Jaunty I don't have modified this option.

---

