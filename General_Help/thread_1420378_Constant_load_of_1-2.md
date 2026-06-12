---
title: "Constant load of 1-2"
date: 2010-03-03
forum: General Help
---

### Post by BBQNinja on 2010-03-03
My laptop running ubuntu 9.10 load NEVER drops below 1, and generally hovers between 1 and 2.  This does not happen on any other of my ubuntu machines.

Any ideas of what to check?  I've turned off indexing and watched system monitor.  I always sit at 0% cpu usage, no active apps, but always a high load.

Attached is a screenshot showing top (with the load).

In my system monitors up  top you can see the middle one in red, which is load.  Constantly 1-2.  The left one is cpu (almost no usage at all) right right one is disk IO.

---

### Post by rnerwein on 2010-03-03
hi
i can't see absolutely no problem at your screen shot. the system is still 96% idle. that means it has nothing to do ( can say boredom ).
ciao

---

### Post by BBQNinja on 2010-03-03
> **rnerwein said:**
> hi
i can't see absolutely no problem at your screen shot. the system is still 96% idle. that means it has nothing to do ( can say boredom ).
ciao

That's exactly the problem.  CPU is idle, but load average is very high.  As I'm typing this it's 2.2.  That means that there are 2.2 tasks in the thread queue waiting for execution.

The most common cause that I've seen for this is an IO problem (processes starved by disk slowness), but I'm not seeing constant IO either!

It's not normal, and thus is a worry.  It really worries me that top doesn't show any active processes.... does that point to something hiding a process?

---

### Post by rnerwein on 2010-03-04
hi
did you have already have a look at /proc/loadavg ( cat /proc/loadavg ). and also use: man proc
this will give you a detail explanation where your load is coming from - there are more than 3 values !
hope this will help you to figure out what's going on because you even can see there the process wich creates the most kernel threads. even top shows you e.g. in your screen shot 148 tasks - you will see in /proc/loadavg  there are more.  ( i guess about 200 )

ciao

---

### Post by robert shearer on 2010-03-04
```
sudo apt-get install iotop
```

then run iotop alongside top

This will show the read/writes and disk load.

May be another way of finding what it is causing load ??

---

