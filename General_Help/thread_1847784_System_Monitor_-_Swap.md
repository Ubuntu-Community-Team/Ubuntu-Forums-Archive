---
title: "System Monitor - Swap"
date: 2011-09-21
forum: General Help
---

### Post by amhainen on 2011-09-21
I'm running 10.04 and I added the system monitor to the panel showing 6 graphs including the processor, memory, network, swap, load, and disk. It's fun to watch an looks cool, but one thing I've noticed is that the swap ALWAYS has zero activity. Just for reference, I have 8GB of ram, so I used an 8GB swap partition when I installed. Should there be any activity there? Is activity (or no activity there) bad?

I looked at the [SwapFAQ]("https://help.ubuntu.com/community/SwapFaq") and from what I can tell, with 8GB of ram, the probability or frequency of having insufficient unused physical memory available will be pretty slim. But, I do usually allocate 2 or 3 gigs to WinXP virtualbox.

Thanks for any comments/explanation.

EDIT: I don't use hibernate either.

---

### Post by patryk77 on 2011-09-21
The system will generally use RAM before it uses swap, as it is much MUCH faster to write to RAM than to swap (hard drive).

As long as your memory usage stays below the 8 GB, it is normal for Swap to go unused...

You should be happy ;) ... This means your computer will be faster.

---

### Post by amhainen on 2011-09-21
> **patryk77 said:**
> The system will generally use RAM before it uses swap, as it is much MUCH faster to write to RAM than to swap (hard drive).

As long as your memory usage stays below the 8 GB, it is normal for Swap to go unused...

You should be happy ;) ... This means your computer will be faster.

Cool, thanks! That was my hunch, just wanted to verify.

---

