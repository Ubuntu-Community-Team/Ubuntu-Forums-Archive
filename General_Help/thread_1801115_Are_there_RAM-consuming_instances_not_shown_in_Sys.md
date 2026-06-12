---
title: "Are there RAM-consuming instances not shown in System Monitor?"
date: 2011-07-09
forum: General Help
---

### Post by 3602 on 2011-07-09
I have 3.5GB of usable RAM as reported by System Monitor.
Now after a couple of hours, System Monitor shows that around 52% of my RAM is being consumed.
Switching to Processes (I have All Processes selected), I see *firefox-bin* consuming around 200-250MB of RAM while *Xorg* consumes around 100-140MB. The rest adds up to another 200MB consumed.
So it doesn't add up. Yeah, I can grab another RAM block and be done with it (giving a projected total usable RAM of 7.0GB, I have another slot). I just want to know where the rest of the consumed RAM is, or am I really bad at doing summations in my head.

Thank you very much.

---

### Post by 1clue on 2011-07-09
Linux uses RAM as a disk cache.

I just upgraded from 10.04 so I don't have everything set up.  Before I had a memory applet in the menu bar that showed what was being used as regular applications, what was being used as swap and how much was used as disk cache.  If I could figure out how to get my menu set back up, I would have that applet again.

---

### Post by wildmanne39 on 2011-07-09
Hi, you can try top it will show a lot more processes then the system monitor.

---

### Post by 3602 on 2011-07-10
Well, in that case it may be worth another 3.5GB just to decrease disk thrashing.

EDIT: Here be *top* output.
```
Mem:   3794576k total,  2320936k used,  1473640k free,    67300k buffers

```

---

### Post by wildmanne39 on 2011-07-10
> **3602 said:**
> Well, in that case it may be worth another 3.5GB just to decrease disk thrashing.

EDIT: Here be *top* output.
```
Mem:   3794576k total,  2320936k used,  1473640k free,    67300k buffers

```
Hi, that should have showed you a lot of process where you can see what is using the most memory, and if there is a program that might be malfunctioning, that was not the only thing it showed was it?

---

### Post by 3602 on 2011-07-10
Unfortunately for me I do not understand its output. I will read MAN pages when I have sufficient time and motivation. Thank you for your answers.
Temp SOLVED.

---

### Post by 1clue on 2011-07-10
You probably want to look at how Linux memory management works too.

Linux always seems pretty close to full except when you have stupid amounts of memory.

---

### Post by wildmanne39 on 2011-07-10
> **3602 said:**
> Unfortunately for me I do not understand its output. I will read MAN pages when I have sufficient time and motivation. Thank you for your answers.
Temp SOLVED.
Hi, your welcome anytime.

---

### Post by deserthowler on 2011-07-10
On the System Monitor in 10.04 it shows 418 used whereas 'free -m' shows 1049 used.  The difference is buffers and caches.

Earl

---

