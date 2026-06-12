---
title: "Periodic freezes"
date: 2010-06-19
forum: General Help
---

### Post by jkounis on 2010-06-19
Every so often, my Ubuntu machine freezes completely: the mouse refuses to move, the keyboard is unresponsive, and a "top" running on a terminal stops updating. The freeze lasts 10-120 seconds, after which everything returns to normal.

If "top" runs during the freeze, when the system comes back to life, it shows an incredibly high load average (30-60). It then slowly settles back down to normal of around 1-2.

What could be causing this sudden spike in load average that renders the system unusable? 

I have a a hypothesis that it might have something to do with swap usage. Whenever the system does come back, I tend to notice the "Swap:" usage at the top of the "top" screen has changed by a couple hundred MB. On the other hand, I would think that Ubuntu's memory/swap file management would be more sophisticated than to freeze the entire machine each time swap needs to be expanded. 

Could this be what is happening, or is it possible that I have some other problem?

I am running 9.04 Jaunty on a Core 2 Duo E6600 with 6GB ram and an 8GB swap file (note: it is not a swap partition. Just a swap file on / )

Thanks!

---

### Post by jkounis on 2010-08-09
I'm bumping this thread, since the problem is still occurring. During a recent freeze, when top came back to life, it showed the load average around 120. This seems extremely high, since it typically averages 1-3.

Any ideas why the system would periodically freeze?

---

### Post by jkounis on 2010-08-11
Maybe I'll rephrase my question:

Has *anyone* had periodic freezes where the computer is unresponsive for a few seconds up to a minute or two, possibly when the swap space is getting increasing or decreasing?

This problem has been annoying me for months, and I'd like to know if it's normal for Linux to do this, or if I need to troubleshoot some more.

THanks!

---

### Post by xscd on 2010-08-17
I really have no idea, but it seems that some people are having problems with the proprietary Nvidia video card driver. Have you tried disabling your video card driver (to use the more generic open-source driver instead), under System--> Administration--> Hardware Drivers ?

Just a thought--

---

