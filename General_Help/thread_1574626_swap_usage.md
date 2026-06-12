---
title: "swap usage"
date: 2010-09-14
forum: General Help
---

### Post by TNT1 on 2010-09-14
Can you dictate what apps use RAM and which ones use SWAP?

---

### Post by kerry_s on 2010-09-14
why? swap is for inactive cache(cache moved out of ram). no active programs use swap.

---

### Post by TNT1 on 2010-09-14
> **kerry_s said:**
> why? swap is for inactive cache(cache moved out of ram). no active programs use swap.

So if I start Evolution, and send some mail, then minimise it, and use OO or something, dose evo move to swap?

---

### Post by 3Miro on 2010-09-14
> **TNT1 said:**
> So if I start Evolution, and send some mail, then minimise it, and use OO or something, dose evo move to swap?

It will, but only if you open a bunch of other stuff and run out of memory. No application gets moved to swap, unless you are running out of memory.

---

### Post by jbrown96 on 2010-09-14
Data is only moved out of RAM when the kernel runs low on memory. The threshold is determined by your swapiness. See [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You really don't want minimized apps to flush all data to swap. Terrible user experience.

---

### Post by Rubi1200 on 2010-09-14
For something a bit more detailed:
[http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

---

### Post by TNT1 on 2010-09-14
> **jbrown96 said:**
> Data is only moved out of RAM when the kernel runs low on memory. The threshold is determined by your swapiness. See [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You really don't want minimized apps to flush all data to swap. Terrible user experience.

Right. Thanks. I have actually used that FAQ before, but missed this bit.

---

### Post by bodhi.zazen on 2010-09-14
> **Rubi1200 said:**
> For something a bit more detailed:
[http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

Excellent link for the "intermediate" Linux user.

---

### Post by TNT1 on 2010-09-15
> **bodhi.zazen said:**
> Excellent link for the "intermediate" Linux user.

It certainly is.

(ps, like your sig, I actually met the Archbishop Emeritus once - he wasn't yet an Archbishop though...)

---

