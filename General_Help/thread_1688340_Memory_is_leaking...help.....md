---
title: "Memory is leaking...help...."
date: 2011-02-15
forum: General Help
---

### Post by Cr0n_J0b on 2011-02-15
Hey everyone.

I'm running the latest version of Ubuntu with Kernel 2.6.35-25-generic as a guest on ESX.  I have vmware tools loaded and I thought all was well, but I'm noticing that the system is eating up a ton of memory.

             total       used       free     shared    buffers     cached
Mem:          3808       3626        181          0        175       2997
-/+ buffers/cache:        453       3355
Swap:         4204          0       4204


I'm looking at top and the biggest memory user is xorg

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1037 root      20   0  162m  42m  10m S    2  1.1   4:53.31 Xorg     

there are a lot of other items in the list but they are all really small too.  all less that .4%

What am i missing?...other than my memory...

---

### Post by blueridgedog on 2011-02-15
Free memory is wasted memory.  If the system is not using swap, which yours is not, then I generally don't worry.  The system will attempt to use available memory so that it is responsive.  This involves caching as many items as possible.

---

### Post by Slim Odds on 2011-02-15
This should be a sticky and forced reading before anyone is allowed to install linux.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Bottom line: You don't have a problem and neither does linux.

---

### Post by blueridgedog on 2011-02-15
> **Slim Odds said:**
> This should be a sticky and forced reading before anyone is allowed to install linux.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Bottom line: You don't have a problem and neither does linux.

Nice link.  I added it to my forum sig.

---

