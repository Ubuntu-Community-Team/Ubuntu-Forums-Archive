---
title: "Best price-benefit processor for desktop running 7 desktops virtual machines"
date: 2011-05-12
forum: General Help
---

### Post by vcrpcant on 2011-05-12
Hi,

I'm looking forward to buy a new desktop computer.
I want to run Ubuntu 10.04 with virtualbox running 7 virtual machines (4 xp and 3 ubuntu).

I'd like to hear some advices about the processor:
Best price-benefit processor for desktop running 7 desktops virtual machines?

Feel free to advice ram also :)

---

### Post by Hedgehog1 on 2011-05-12
> **vcrpcant said:**
> Hi,

I'm looking forward to buy a new desktop computer.
I want to run Ubuntu 10.04 with virtualbox running 7 virtual machines (4 xp and 3 ubuntu).

I'd like to hear some advices about the processor:
Best price-benefit processor for desktop running 7 desktops virtual machines?

Feel free to advice ram also :)

Your main 'pinch point' performance wise is I/O rather than the processor.  One of the AMD 4 or 6 core CPUs will be fine (or an i7 if you prefer Intel - both work very well). A 6 core is preferred, but RAM is more important.

RAM will be where you get you best benefit.

Assuming you use Ubuntu as your 'host' OS, you will need 1 gig of ram for each session of Ubuntu - 1 host & 3 guests = 4 gigs.

4 XP sessions will each need 2 gigs of RAM, adding the need for 8 more.

This brings you to 12 gigs.

To allow growth over time, I would select a motherboard that supports at least 16 gigs of RAM and fully populate it with the fastest RAM the motherboard can support WITHOUT over clocking.

SATA-III (6 gbit) controller and SATA-III Hard drive(s) would also be a big help.

With a solid high-speed I/O foundation, you will have the best chance of good performance.

**The Hedge**

:KS

---

### Post by vcrpcant on 2011-05-13
Your post was very enlightening! Thank you, The Edge :)

---

