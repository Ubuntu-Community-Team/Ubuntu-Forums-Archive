---
title: "Kernel panic - Mercurial clone - eeePC 1005HA"
date: 2011-02-01
forum: General Help
---

### Post by Dauthi4 on 2011-02-01
Hi,

Each time I try to do a hg clone on my eeePC 1005HA, I've got a kernel panic.

I've tried with different kernels, different versions of Mercurial (I tried to compile from source), even on a live USB version of Ubuntu.

I've ran tests on memory and hard drive, but it seems ok.

The messages were :

Kernel panic - not syncing : Fatal Machine check
Machine check Exception
Processor context corrupt

swapper tainted
kworker tainted
python tainted

My current kernel is : 2.6.37-020637rc2-generic

It works sometimes (like 1 in 10).
It works like a charm on my desktop computer (Ubuntu 64 bits), on Windows XP and on a openSuse live usb.

I don't know what else to do, any ideas ?

---

### Post by Hauke on 2011-04-23
Hi,

I have the same Problem with my 1005HA. I have not tried Mercurial but with git I get a MCE. 
When I do "git clone http://www.project-moonshot.org/git/libeap.git" it results in a kernel panic. When the system is under load, like it compiles some Linux kernel, and I do this git clone then it does not result in a kernel panic.

I do not have a solution for this problem, do you have one? Do you still have warranty and want to send it back to your dealer?

---

