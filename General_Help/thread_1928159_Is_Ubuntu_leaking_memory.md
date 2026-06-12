---
title: "Is Ubuntu leaking memory?"
date: 2012-02-19
forum: General Help
---

### Post by alexei_ on 2012-02-19
After having system up for 23 hours I have closed all programs except for "byobu" and "vim". I got:

> 
htop: 2420/3707MB       65%  

             total       used       free     shared    buffers     cached
Mem:          3707       2624       1082          0          5        209  
-/+ buffers/cache:       2409       1297 
Swap:            0          0          0
However after restart with the same applications running I got:
> 
htop: 723/3707MB        20%  
             total       used       free     shared    buffers     cached
Mem:          3707       1105       2602          0        145        342  
-/+ buffers/cache:        617       3089 
Swap:            0          0          0
The question is: Why I was missing 45% (!!!) out of my memory before restart?

Using all standard tools (ps/top/htop/free) I could not find any process(es) that could consume such amount of memory.

There is also another problem which I have already reported in other threads (with no solution so far): After memory usage gets to 80%+ the system start hanging for about 7-15 minutes showing intensive HD usage (based on indicator on my laptop). I have disabled swap, so it is not swapping. Using iostats did not reveal any excessive disk usage.

So the user experience with this Ubuntu system is horrible. Windows XP Home edition on 6 years old hardware was working MUCH BETTER.

I have seen similar problems reported, but there are no solutions. Also I have spend time reading "Ubuntu User Manual" (or how it is called) -- it is horrible simplistic and does not give you any direction on how to research and troubleshoot this kind of problems.

---

### Post by cottfcfan on 2012-02-19
What DE are you using?
Gnome-Shell, Unity, or something else.

---

### Post by zero2xiii on 2012-02-19
Hay,

I had a similar problem on my laptop, however it is NOT a linux/Ubuntu bug, rather BIOS.

Check you BIOS for "Caching", "Shadowing", "Precache" and "Post Cache" and disable them all (or any one of them you do find). Mine had a Cache and Pre Cache option (selectable between the two and disable). Putting it on disable removed my "memory leak".

Cherz

---

### Post by alexei_ on 2012-02-19
It is "Unity". Also
> 
uname -a
Linux nv53lx 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

But the problem is get the tools for troubleshooting. Mentioned tools do not help.

---

### Post by wildmanne39 on 2012-02-19
Deleted

---

### Post by cottfcfan on 2012-02-19
Unity on my Computer, is not leaking memory.
How much memory do you have?
Memory will be cached as is mentioned, this isn't a problem, but memory usage jumping from 20% to 80% is not normal.

---

