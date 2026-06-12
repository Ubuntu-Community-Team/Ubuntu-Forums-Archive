---
title: "Xorg massive memory usage"
date: 2010-02-02
forum: General Help
---

### Post by EndingPop on 2010-02-02
I'm having an issue with Xorg using a ton of memory. To start off, here are the machine specs:

Dell Precision M4400
4 GB of RAM
Dedicated video card with onboard video RAM
Running Ubuntu 9.10 x64
Not using Compiz or any special display effects.

Results of "X -version":
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux marcus-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=dc474f24-3833-4896-bd3e-0a209d66a767 ro vga=799 quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
```


I'm using this machine for thesis research, and that involves running some niche software and some of my own code. The crux is that many folders and files are created and deleted over the course of 30 seconds. These runs take several days to complete.

The problem is that if I start out with a fresh log in Xorg starts at about 30 MiB in use. After letting my program run overnight, Xorg is typically using several GiB of memory, pushing the amount in use up about 95%. Normally I can do regular web browsing while my program runs, but when the memory usage is that high the whole machine is unusable, and my research program slows a lot.

So what I'm actually running is a bash script that calls a commercial optimization code ([HEEDS]("http://www.redcedartech.com/products/heeds_professional")) several times in sequence, which in turn calls Matlab and some very small C programs of mine many times as well. So no instance of my code or HEEDS is running the entire length of time, since they end and new instances begin many times. That fact, and that I've run this same thing on other Linux platforms and Windows without issue makes me think that this is unrelated to the code I'm running. Perhaps it's exacerbated by the many folders and files that are created over the course of the program's run.

So what do I have to do prevent Xorg from stealing all of my memory?

---

### Post by EndingPop on 2010-02-03
Something I left out was that the swap sits at about the same level the entire time (very low).

Solutions, anyone?

---

### Post by t4thfavor on 2010-02-03
There is a thread called Memory Leak on the first two or three pages that may shed some light.

Search for it, as I haven't seen it since mid yesterday.

---

### Post by EndingPop on 2010-02-03
The "Memory Leak" thread seems to think it was a problem with the ATi driver bundled with Ubuntu. I'm using an nVidia card with EnvyNG to get the proprietary drivers. Using version 185.18.36.

---

### Post by EndingPop on 2010-02-03
There appears to be a bug report on this issue [here]("https://bugs.launchpad.net/xorg-server/+bug/484521").

---

### Post by rev22 on 2010-03-13
Quick hack-ish fix: memory usage limit for X

Add the following two lines to /etc/security/limits.conf

root soft data 30000000

root hard data 60000000

Worked for me, no more 100s of Mb used by Xorg and massive swapping to HD partition!  It would happen when using large X clients like firefox and wine.

Enjoy free software, ciao,
Michele

---

