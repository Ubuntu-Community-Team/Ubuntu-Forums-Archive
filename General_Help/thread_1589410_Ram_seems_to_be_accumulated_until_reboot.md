---
title: "Ram seems to be accumulated until reboot"
date: 2010-10-06
forum: General Help
---

### Post by Quackers on 2010-10-06
I am posting here rather than in the Maverick Meerkat section because this happened in Lucid too.
I have just rebooted my system and ram usage is at 16% (of 2GB) whilst nothing is running other than desktop and Compiz. However if I leave the system running for 2 days (just using suspend from time to time) the ram usage will increase to 25 or 26% at idle. This will reduce again to 16% after a reboot.
In short it seems that some processes are not fully releasing the ram they use and there is a build up of wasted ram.
Does anybody else notice anything similar? Does anybody have any suggestions as to how to nail down the offending processes? Can anything be done about them if I find them?
Thanks :)

---

### Post by amauk on 2010-10-06
RAM isn't much good if it's not being used
RAM that is "unused" will be used for caching

How are you measuring RAM usage?

```
tony@tony-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3961       3614        346          0         93       2067
-/+ buffers/cache:       1453       2508
Swap:        10385         12      10373
```

You need to be looking at the "-/+ buffers/cache" line for the amount of RAM used that is not just cache

---

### Post by Quackers on 2010-10-06
I appreciate what you're saying.
I have been using Conky display to monitor ram usage, which has agreed with the output of System Monitor.
free -m seems to agree too.

---

### Post by SeijiSensei on 2010-10-06
See [http://ubuntuforums.org/showthread.php?t=1587461](http://ubuntuforums.org/showthread.php?t=1587461)

Linux will eventually use all your memory, largely to cache disk files it's read.  That's a good thing from a performance standpoint.  Most of my machines eventually have >90% of memory in use, mostly for caching.

---

### Post by Quackers on 2010-10-06
Thanks for that. I'll leave it on for a couple of weeks to see how high I can get it :-)
What you say does make sense. The more that is cached the quicker the programs open I suppose.

---

### Post by Crazedpsyc on 2010-10-06
to clean the memory BleachBit is a good option, so open a terminal and run:
```
sudo apt-get install bleachbit
sudo bleachbit
```
then check all the options except Places (under firefox) and Free Disk Space (under system) and run it.
the memory option (although experimental) does a good job of clearing unnecessary caches in the RAM
this does have some risks, but I have never experienced a problem with it

---

### Post by Quackers on 2010-10-06
Thanks Crazedpsyc, if things get too much for me I'll take a look at bleachbit.

---

### Post by renkinjutsu on 2010-10-06
To my memory, Conky's memperc does not account for cache, so the "25%" that it's displaying is the chunk of memory that is being occupied by something.

to op: Do you use Evolution for email or calendars?

---

### Post by kpkeerthi on 2010-10-06
There is no need to clean ram caches (using BleachBit or anything). Kernel will do it when required.

---

### Post by Quackers on 2010-10-06
Yes, renkinjutsu, I use Evolution for email.

---

### Post by renkinjutsu on 2010-10-07
> **Quackers said:**
> Yes, renkinjutsu, I use Evolution for email.

Can you see what's consuming your RAM? I remember a while back when I used to use Evolution to integrate my gmail and google calendars with my desktop, my RAM usage would increase over time, and it was caused by evolution-data-server.. That process had to be killed once in a while. Just wondering if you were in the same situation.

---

