---
title: "What's with Swap Space?"
date: 2010-01-21
forum: General Help
---

### Post by sidewalkcynic on 2010-01-21
I have never seen the swap space monitor indicate any activity - what's up with it?

I don't watch movies, maybe some ten minute YouTube, so if movie buffering is where I would see some activity???

---

### Post by synapsys on 2010-01-21
Swap is only used when you run out of physical memory. If you're not using any swap, that simply means you have plenty of ram.

---

### Post by ubunterooster on 2010-01-21
I've set up my 6Gb RAM desktop w/o any swap space. Unless you run out of ram, you don't even need to install it.  You can upgrade your RAM to 2Gb and reinstall w/o swap space if you want to free up that space.

---

### Post by jamesisin on 2010-01-21
> **synapsys said:**
> Swap is only used when you run out of physical memory.

That's not 100 per cent accurate.  I have 3.6 GB RAM and typically use about 1.5 GB.  I see my swap size change depending upon system usage.  So swap *is* being used on my system even though I have not reached (or come close to reaching) my RAM limit.

Unless you are hurting for drive space, I see no reason to include a swap partition.  It's not going to hurt and it can assist.

---

### Post by sidewalkcynic on 2010-01-21
Well, thanks - that pretty much answers my question. Maybe, some day in the future, I'll use up my 1Gb of RAM and need to borrow 10 Kb from Swap.

Now that I think about it, my RAM has jumped up a few times, but it then probably used so little of the swap that it barely registered - so i should change the graduation of the monitor.

---

### Post by fragos on 2010-01-21
I almost never use swap with 1GB of memory and swapiness set to 10 in /etc/sysctl.conf. If you wish to hibernate you need a swap area at least the same size as physical memory. I for one wouldn't advise eliminating swap space.

---

