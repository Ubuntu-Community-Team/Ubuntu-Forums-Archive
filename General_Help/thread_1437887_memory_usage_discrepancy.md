---
title: "memory usage discrepancy"
date: 2010-03-24
forum: General Help
---

### Post by malkien on 2010-03-24
I am trying to understand a large amount of allocated memory that seems not to be accounted for on my system.
I'll say up front that I am discussing memory usage without cache and buffers, 'cause I know that misunderstanding comes up a lot.

I am in a KDE 4.3 desktop (Kubuntu 9.10), using a number of java apps like Eclipse that tend to eat up a lot of memory.
after a few days, even if I quit most apps, 1 gb of ram remains allocated (out of 2 gb).
this appeared excessive, and I took the time to add up all values of the RES column in htop (for all users).
the result was about 1/2 gb.

am I trying to match the wrong values?
or could some memory be allocated and not show up in the process list?

any suggestion will be greatly appreciated


this is the output of free
```

             total       used       free     shared    buffers     cached
Mem:       2055456    1940264     115192          0     123864     702900
-/+ buffers/cache:    1113500     941956
Swap:      2104504     246416    1858088

```

this is the topmost output from top
```

top - 12:31:00 up 4 days,  1:24,  2 users,  load average: 0.06, 0.06, 0.01
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.4%us,  0.2%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2055456k total,  1931376k used,   124080k free,   123624k buffers
Swap:  2104504k total,   247068k used,  1857436k free,   698888k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2041 michele   20   0  401m  11m 6388 S    1  0.6   1:33.15 yakuake
 2047 michele   20   0  591m  42m  18m S    1  2.1   5:50.41 kopete
 1040 root      20   0  503m 117m 3960 S    0  5.9  74:23.69 Xorg
 1914 michele   20   0  657m  31m  13m S    0  1.6  51:09.98 kwin
 1918 michele   20   0  878m  49m  24m S    0  2.5  30:32.75 plasma-desktop
16882 michele   20   0 19132 1380  980 R    0  0.1   0:00.05 top
    1 root      20   0 19456 1320  784 S    0  0.1   0:02.38 init

```

---

### Post by Intrepid Ibex on 2010-03-24
"Fully working KDE" easily eats up quite a lot of memory. What are your usages immediately after login?

Also I'm not 100% sure whether you know the difference between caching stuff in RAM and actually "using" it. There's quite a lot of places to read about the way linux handles memory but here's one: [http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

---

### Post by cjhabs on 2010-03-24
Your "top" and "free" totals appear to be very close.

Try this command to list the sum of memory used by all the pids on the system:
for pid in `ps -e -o size`; do let var=$var+$pid; echo "$var : $pid"; done

First column gives the running total and the second gives each pid usage.
I found that this gives a higher total than free and top.
Remember to zero out $var if you run this more than once in the same shell.

HTH

---

### Post by malkien on 2010-03-24
does this mean the RES column in top (or better yet htop) does not accurately reflect the allocated memory?

---

### Post by rnerwein on 2010-03-24
hi
buffers and cache is about nearly 1GB ( dentries and inode cache ) that's ok.

the fastest IO is no IO !

ciao

---

### Post by malkien on 2010-03-25
I made it clear in my first post that I'm not counting cache and buffers, just the memory allocated to applications.
I cannot seem to find a correspondence between that total and the amount declared for single processes

---

### Post by malkien on 2010-04-06
> **Intrepid Ibex said:**
> "Fully working KDE" easily eats up quite a lot of memory. What are your usages immediately after login?


I checked after a reboot and my fully working KDE uses about 350 megs after login.
that means more then 500 extra after I shut down all applications and get back to the same condition.

---

