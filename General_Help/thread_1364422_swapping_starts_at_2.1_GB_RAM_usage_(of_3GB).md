---
title: "swapping starts at 2.1 GB RAM usage (of 3GB)"
date: 2009-12-25
forum: General Help
---

### Post by corck on 2009-12-25
Hi,
I'm running on Kubuntu 9.10 (64bit). I have a dell vostro with 3 GB of RAM and 4 GB of SWAP setup.

I experience that whenever I come up to 2.1 GB of RAM usage, Kubuntu starts to swapping and never uses the full 3GB of RAM.
Interestingly for each 100 MB of additional RAM usage (looking at the KDE Systemmonitor) another 100MB of SWAP gets used. So at 2.4 GB RAM I have 300 MB of SWAP usage.

Is this the correct behaviour or is this a bug? Another thing is, that when I close most applications and the RAM usage is below 1 GB again, there's still now 270 MB of SWAP used.

Is there a way to tell Kubuntu to use the full 3GB and start swapping at 3GB??

---

### Post by MaxIBoy on 2009-12-25
Interesting... you may have luck if you disable suspend.

Also, try this as an experiment. Temporarily turn off swap:
```
sudo swapoff -a
```And try pushing your RAM usage up as high as possible.


Overall, though, this shouldn't be an issue unless you're worried about wear and tear on your disk. The scheduler is pretty good at only putting inactive stuff on the swap partition, so you really don't notice too many slowdowns. Maybe look at how much RAM is being used as cache? Because a lot of RAM monitors don't show that in your RAM usage. Generally, the kernel tries to go for 100% RAM usage by filling unused space with cache. Caching a few things in memory can speed up the system a lot more than the performance you loose by swapping a few other things. Caching things to swap obviously makes no sense, so I imagine that cache probably stays in RAM...

---

### Post by falconindy on 2009-12-25
Change your swappiness! In /etc/sysctl.conf, add the following lines:

```
vm.swappiness=1
vm.vfs_cache_pressure=10
```
The lower the swappiness, the less likely you are to use swap over available RAM.

---

### Post by corck on 2009-12-28
@MaxIBoy:
turning swap off, works fine. everything is loaded into memory and works fine then. However does not solve my problem.

@falconindy: I added your settings (haven't looked up what the exactly do). It seems not to solve the problem. When I start up my virtual machine as a test, it starts swapping again. Now having 2.6GB in RAM (which is more than my 2.1 before, however have already 150MBs in Swap. The problem is that it swaps programs like Firefox onto Swap, so switching between Firefox and Virtualbox is cumbersome, at least for the first time. Then it loads it back to memory.

The whole system however is definitely slower when switching between tasks even if there's still ~400MB RAM left.

anyone another idea?

---

