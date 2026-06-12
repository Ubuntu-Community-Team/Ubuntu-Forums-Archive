---
title: "Is this high memory usage normal?"
date: 2010-05-26
forum: General Help
---

### Post by Rackstar on 2010-05-26
Hey,

I bought a new Dell Studio 15 ( 1558 ) and did a fresh install of Ubuntu Lucid, but this doesn't seem to be very lightweighted! 

At a fresh boot, only apps open: gwibber, firefox and gnome-system-monitor uses about 1.3 GB! 

My specs:
Intel i5 processor
ATI HD5470 dual screen
4GB DDR3 memory

See screenshots for gnome-system-monitor output.

For reference, these are the system requirements for Ubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) :
> # 1 GHz x86 processor
# 512 MiB of system memory (RAM)
# 5 GB of disk space
# Graphics card and monitor capable of 1024x768
# CD-ROM drive


Thanks!

EDIT: I've added a screenshot of system monitor with option "Show All Processes", this shows that Xorg uses about 202 MB.

---

### Post by NT4usB on 2010-05-26
From what I've read, Linux uses memory instead of caching processes... way faster.
It allocates up to 85-90% of available memory and divides it up among the processes.
As processes are added and subtracted, it will reallocate as required.

0.60, 0.74, 0.63 does seem a bit high though, for a fresh boot and nothing open.
I usually see single digits to teens on an idle system.

---

### Post by bodhi.zazen on 2010-05-26
Linux is not Windows and unused RAM is wasted RAM.

See:

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

---

### Post by sylvester_0 on 2010-05-26
Run "free -mo" at a terminal to see "actual" memory usage. Anything above that is just cache (disk etc.) Leave a Linux system running long enough and it will use all the RAM it can get - this is not a bad thing.

---

### Post by howefield on 2010-05-27
> **Rackstar said:**
> At a fresh boot, only apps open: gwibber, firefox and gnome-system-monitor uses about 1.3 GB!

What is the memory usage on a fresh boot without those applications running ?

I tend to see see about 300 megabytes on 32 bit, and 400 megabytes on 64 bit (give or take a few).

Thereafter the system can do what it likes with the memory, but it doesn't sound right to fresh boot on 1.3 gigabytes, imho.

---

### Post by Rackstar on 2010-05-27
Hey!

Thanks for all the answers. I didn't know this about the memory management in linux.

I tried a fresh reboot, and this is what it says:

Between 600 and 800 (says free -mo, but rhytmbox was launched). This is already half of what I reported before, probably my bad...

Still pretty high IMO but I'll probably be wrong.

---

### Post by QIII on 2010-05-27
Remember, as said above, *nix runs on the assumption that unused memory is wasted memory.
 
My OpenSolaris (Unix) system often jumps up to 90% of available memory "used" almost immediately.  It's sometimes better to call it "ready to be used" in *nix.

---

### Post by Rackstar on 2010-05-27
> **sylvester_0 said:**
> Run "free -mo" at a terminal to see "actual" memory usage. Anything above that is just cache (disk etc.) Leave a Linux system running long enough and it will use all the RAM it can get - this is not a bad thing.

Strange that free always reports a higher usage than gnome-system-monitor.

---

### Post by Rackstar on 2010-05-27
> **QIII said:**
> Remember, as said above, *nix runs on the assumption that unused memory is wasted memory.
 
My OpenSolaris (Unix) system often jumps up to 90% of available memory "used" almost immediately.  It's sometimes better to call it "ready to be used" in *nix.

I was wondering, I have an application of which I know, it reserves 50% of the "free" memory for it's use, some Photographic software. How does this work?

EDIT: I'm trying to find where I read this, I could be wrong, as I've been wrong here before :p

---

### Post by lavinog on 2010-05-27
there is a bug in ureadahead that causes about 128m to be wasted after a profile boot.
You can free this memory with this command:
```

echo 1 |sudo tee /sys/kernel/debug/tracing/buffer_size_kb

```
here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

also use free -m to see what is being used
```


free -m
             total       used       free     shared    buffers     cached
Mem:          1380       1150        229          0         43        678
-/+ buffers/cache:        429        951
Swap:          509          2        507

```
In this example 429M of memory is being used and not cached.

---

