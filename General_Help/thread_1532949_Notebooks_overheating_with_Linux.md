---
title: "Notebooks overheating with Linux"
date: 2010-07-17
forum: General Help
---

### Post by 9tails on 2010-07-17
Anyone else having overheating issues with Linux on notebooks? I own 3 different notebooks equipped with Nvidia, ATI, and ATI + Intel graphic cards.
When I'm using Linux (any distro, including Ubuntu and the more lightweight Lubuntu) the computer starts overheating, the temperature rapidly reaches 50/55° and the fans run loudly.

I don't understand why - there are no particular applications running, no compiz or other 3D stuff, htop shows a very negligible cpu usage, and I also tried with a freshly installed Linux with no no custom settings or applications, it's the same.

As a comparison, when I'm working under Windows (xp or 7) the temperature is ok even after 1 hour, running all kinds of applications.

I tried settings the cpu governor to "conservative" with cpufreq-tools, it worked but the overheating persists.

I wonder if there is some kind of problem with the graphics code in Linux, perhaps causing the gpu to overheat?

I also saw that others have the same problem on other forums, for example this one: [https://bbs.archlinux.org/viewtopic.php?id=85430](https://bbs.archlinux.org/viewtopic.php?id=85430)

Any ideas?

---

### Post by CoolJohnB on 2010-07-17
I have a Dell Vostro 1700 and its running at 46.5C, the fans are working but I never hear them just feel the warm air coming out the side.  Considering the temperature where I live is permanently around 30C I don't think that's too bad? What do you think?

---

### Post by hawthornso23 on 2010-07-17
It might be [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)

There seems to be a problem in more recent versions of the linux kernel to do with load balancing on multiprocessor systems which causes laptops to have lower battery life and run hotter. Load balancing is supposed to ensure that the processing tasks are distributed rationally across the cores. However it seems to be 'trying too hard' to do this. It 'wakes the processors up' around ten times per second to check if the load is balanced, which stops the laptop from powering down one processor to save power and makes it run hot.

The linux kernel people seem to be working on this issue now as you can see [http://www.listware.net/201007/linux-kernel/16253-high-power-consumption-in-recent-kernels.html](http://www.listware.net/201007/linux-kernel/16253-high-power-consumption-in-recent-kernels.html) . We just have to wait for them to fix the problem. In the meantime if this is a serious issue for you, then you might want to consider rolling back to an earlier version of the kernel which is not afflicted with this bug.

---

### Post by 9tails on 2010-07-17
Very interesting, thanks hawthornso23. This make a lot of sense, I almost forgot about the number of wakeups reported by powertop in the last months.

So a call to nohz_ratelimit in tick-sched.c code is likely to be the culprit. The 2.6.35 kernel is already in rc5, so I'm going to wait for the final version, hoping they're going to remove that... "feature". If not, I'll just comment nohz_ratelimit out :P

Thanks again!

---

