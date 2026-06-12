---
title: "Is there some odd reason why Ubuntu is using ALL of my ram! ?"
date: 2010-07-25
forum: General Help
---

### Post by WhatTheHell? on 2010-07-25
Ubuntu 10.04.1 LTS

top - 20:19:35 up  2:52,  3 users,  load average: 1.94, 2.23, 2.22
Tasks: 187 total,   4 running, 183 sleeping,   0 stopped,   0 zombie
Cpu(s): 68.7%us, 10.3%sy,  0.0%ni, 21.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4124600k total,  3980068k used,   144532k free,   191228k buffers
Swap: 10586792k total,     8292k used, 10578500k free,   838184k cached

ATI video card drivers.
Not much is open by the way.  Aka, it is ubuntu and not firefox etc.

---

### Post by themusicalduck on 2010-07-25
When Ubuntu says that it is using all of your ram, it is actually saying that the ram is cached. That is, it is made ready to be used by programs when you load them, or some such.

To actually find out how much is being used, type ```
free
```into a terminal and look at -/+ buffers/cache:

---

### Post by WhatTheHell? on 2010-07-25
razux@razux-core:~$ free
                     total          used            free     shared    buffers      cached
Mem:       4124600    3801692        322908             0   123812    1109280
-/+ buffers/cache:     2568600      1556000
Swap:    10586792        13840    10572952


So... I'm guessing this isnt normal right? because it says used 3801692 out of 4124600?
System monitor says its using 30% for cache and 60% for programs.  That 60% will be a 70% here in a little bit though.

I'm still guessing something's wrong.  On startup or with the ati video card drivers removed, it uses only 600 mb of ram.  Now it uses 3.9gb of my 4 gb of ram.

---

### Post by CharlesA on 2010-07-25
> **WhatTheHell? said:**
> razux@razux-core:~$```
 free
                     total          used            free     shared    buffers      cached
Mem:       4124600    3801692        322908             0   123812    1109280
-/+ buffers/cache:     2568600      1556000
Swap:    10586792        13840    10572952
```


So... I'm guessing this isnt normal right? because it says used 3801692 out of 4124600?
System monitor says its using 30% for cache and 60% for programs.  That 60% will be a 70% here in a little bit though.

I'm still guessing something's wrong.  On startup or with the ati video card drivers removed, it uses only 600 mb of ram.  Now it uses 3.9gb of my 4 gb of ram.

It's perfectly fine.

Linux caches memory when it's not in use. It's not being used but it is cached so that it can be used.

This is what mine looks like:

```
charles@thor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       4855       1126          0        130       **4294**
[COLOR="Red"]-/+ buffers/cache:        430       5550[/COLOR]
Swap:        12401          0      12401

```

Mine is only using 430MB of RAM with 5550 MB free.

---

### Post by linux18 on 2010-07-26
goto system monitor and click the memory column to sort the list by memory, if anything is using over 75MB except FF, wine, virtualbox then you may have a leak and should post that program here for analysis.

---

### Post by nmaster on 2010-07-26
> **linux18 said:**
> goto system monitor and click the memory column to sort the list by memory, if anything is using over 75MB except FF, wine, virtualbox then you may have a leak and should post that program here for analysis.

try running this from the command line: ```
 ps -e -orss=,args= | sort -b -k1,1n | pr -TW$COLUMNS

```that'll list your processes by memory usage. the number is in KB

---

### Post by CharlesA on 2010-07-26
I doubt there is a memory leak. If you take a look at the output of this:

```
free -m
```

Then look at what it says after -/+ buffers/cache, that will tell you how much memory is actively being used and how much is free.

---

### Post by nmaster on 2010-07-26
> **CharlesA said:**
> I doubt there is a memory leak. If you take a look at the output of this:

```
free -m
```Then look at what it says after -/+ buffers/cache, that will tell you how much memory is actively being used and how much is free.

that's probably true.  it looks like approx. 1.5 GB of the ram is being used.  there are probably just a couple memory intensive programs running. if there is a leak, then its probably with one of those programs, not actually with ubuntu.  in any case, its still good to know whats going on.

---

### Post by mc4man on 2010-07-26
Those numbers don't look that good - you shouldn't be using 2.5 Gb or so and be into your swap.
I'd do a reboot, (may be related to ureadahead), and run free -m again

( if posting results,  highlight and then put into a 'code box', will keep things lined up.

---

### Post by dcstar on 2010-07-26
> **CharlesA said:**
> It's perfectly fine.
..........

Yep, every few weeks a "panic" thread like this pops up that has been now answered hundreds for time previously, I am surprised that people still have the tolerance to continually answer these non-problems for those that don't search out the previous threads.

---

### Post by WhatTheHell? on 2010-07-29
> **dcstar said:**
> Yep, every few weeks a "panic" thread like this pops up that has been now answered hundreds for time previously, I am surprised that people still have the tolerance to continually answer these non-problems for those that don't search out the previous threads.


I spent hours searching threads and found nothing that said it was normal.

---

### Post by WhatTheHell? on 2010-07-29
In fact.  I've found that when I remove the ATI video card drivers, the used ram goes from 3.9 GB to 600 mb.

---

### Post by WhatTheHell? on 2010-07-29
top - 15:16:30 up 4 days, 17:57,  4 users,  load average: 0.93, 1.01, 1.12
Tasks: 205 total,   1 running, 204 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.1%us,  6.5%sy,  0.2%ni, 60.6%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4124600k total,  3825344k used,   299256k free,    77024k buffers
Swap: 10586792k total,   278596k used, 10308196k free,   520680k cached



This still doesn't seem right to me... but I guess if you say so....

---

