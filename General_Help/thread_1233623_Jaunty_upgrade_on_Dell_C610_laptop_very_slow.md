---
title: "Jaunty upgrade on Dell C610 laptop very slow"
date: 2009-08-06
forum: General Help
---

### Post by Michl on 2009-08-06
I upgraded from Intrepid to Jaunty on a Dell C610 laptop and
Jaunty compared to Intrepid is very slow and hot.  CPU runs
at or close to 100% all the time and the temp is always around
45 - 55 C.  Performance in intrepid was much faster and cooler
running the same software.  (Memory is 502MiB)

Any remedies for this before I reinstall Intrepid?

---

### Post by xyphur on 2009-08-06
I also have a C610 running Jaunty, and it's been fine... Of course, my machine is essentially maxed out in terms of upgrades though. 1.2GHz P3, 1GB PC133, 60GB 7200 ATA/133, and I ordered an Inspiron mainboard and swapped the nVidia Geforce2Go 32MB graphics board in place of the 16MB ATI Radeon M6 LY and have a Sharp 1600x1200 LCD panel in place of the stock 1024x768 Hitachi one. What speed CPU is in that thing at the moment?

Aside from CPU, I think you might want to look into RAM.

Also, for the record I did a fresh install of Jaunty on it, not an upgrade. Maybe this could be a partial source of issues?

---

### Post by BZF on 2009-08-06
[SIZE=1]Its sorta the same idea as windows like the newer version will be slower depending on specs. Try doing a new installation or downgrading back to 8.10[/SIZE]

---

### Post by xyphur on 2009-08-07
> **BZF said:**
> [SIZE=1]Its sorta the same idea as windows like the newer version will be slower depending on specs. Try doing a new installation or downgrading back to 8.10[/SIZE]

In all actuality, Linux in general basically ignores that rule-of-thumb and typically becomes more efficient with each new revision. At worst, you'll notice no speed improvement, assuming running applications and services remain identical between old and new revisions.

Of course, if you toss in a couple new features that consume more RAM than was being used by the older version, you will of course see a decline in performance. The same can be said about any OS though, and this is what sets Linux apart from it's competition. The ability to be modular. What you don't need can be removed. Try recompiling the NT kernel in Windows to achieve the same result...

I do agree that a fresh install of 9.04 is in order though.

---

### Post by Michl on 2009-08-07
> **xyphur said:**
> 
I do agree that a fresh install of 9.04 is in order though.

I'll give that a whirl, although Intrepid was an upgrade from
Hardy and it worked like a charm.  (Hardy, on the other hand,
was a fresh install after a mediocre upgrade.)

---

### Post by Michl on 2009-08-07
Did a fresh install of Jaunty and it still runs hot and slow on
this C610 compared to Intrepid.  Speed is 1GHz, by the way.

For what it is worth, kernels and xorgs change in size and
computational demands.

ADDED:
Returned to Intrepid with a fresh install and the C610 runs
fine again.  CPU is not at 100% almost all the time and its
temp is normal.  By the way, I checked Processes and in Jaunty
xorg used over 30% of the CPU all the time and in Intrepid
xorg uses between 9 and 22%.  So it seems that Intrepid might
be the last stop on this laptop.

---

