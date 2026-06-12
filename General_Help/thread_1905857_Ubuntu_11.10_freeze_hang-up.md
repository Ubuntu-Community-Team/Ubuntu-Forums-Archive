---
title: "Ubuntu 11.10 freeze hang-up"
date: 2012-01-07
forum: General Help
---

### Post by alexei_ on 2012-01-07
I am having this issue for long time with my laptop. 
After some time after fresh restart (on 2nd, 3rd day) the system periodically hangs up. 
It does not respond to mouse or keyboard, timer (with seconds) stops and Hard Disk is in use. It may take 20 seconds to several minutes for system to start being usable again.

Well, finally I came to conclusion that it does not swap (I have disabled it), and has a lot of free memory (800Mb+ confirmed by "free"). I was using dstat, and recently iotop for troubleshooting.

I was able record iotop output durung the freeze.
 The max for read: Total DISK READ: 6.91 M/s
 The max for write: Total DISK READ: 6.91 M/s

If this I/O makes the system to freeze?
Or what is the root cause of the issue?

Is it possible to avoid these freezes?

Another may be important thing, I put my laptop on "Suspend" a couple times per day. After fresh restart with the same applications running  the system work fine -- no freezes (till next "Suspend")

---

### Post by Z06Gal on 2012-01-07
I am also experiencing this.  It occurs multiple times a day and I have tried everything I can think of.  I saw this link on a thread earlier and I this is what is happening in my case:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335)


Please post if you get it solved :D

---

### Post by rsvancara on 2012-01-08
What type of laptop do you have?

---

### Post by alexei_ on 2012-01-14
> **Z06Gal said:**
> I saw this link on a thread earlier and I this is what is happening in my case:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335)


It is similar, important thing -- Hard Drive is in use ALL THE TIME.
Just recent example -- with 
> 
free -m
             total       used       free     shared    buffers     cached
Mem:          3707       2982        724          0          0         29
-/+ buffers/cache:       2952        754
Swap:            0          0          0

uname -a
Linux n53laptop 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


It took 7 MINUTES to open empty google-chrome window. During all this time Hard Disk was intensively used... (why?). Looks like a bug in kernel... 
Do not think it is related to my laptop. It is Gateway NV53.

---

