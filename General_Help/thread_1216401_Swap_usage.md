---
title: "Swap usage"
date: 2009-07-18
forum: General Help
---

### Post by H4F on 2009-07-18
Seems that some of my programs in the long run gets memory leaked.
After few days my swap usage becomes 50% and bigger and bigger. System becomes slow.
to find cpu usage i just use htop.

The question is how do I find which program uses swap memory ?
How do I find program which leaks memory ?

---

### Post by CREEPING DEATH on 2009-07-18
In the GUI:
System --> Administration --> System Monitor
BUT, that only shows the stuff in X.
In the CLI:
```
top
```

CD

---

### Post by credobyte on 2009-07-18
The easiest way would be to use System Monitor ( System -> Administration ) ;)

---

### Post by H4F on 2009-07-18
yeap . but as far as I know htop(top) does not show the swap usage.
If I am wrong can you tell me how do see swap usage with htop ?

---

### Post by LightningCrash on 2009-07-18
/proc/$PID/status

Look at VmLock

---

### Post by jerome1232 on 2009-07-18
> **H4F said:**
> Seems that some of my programs in the long run gets memory leaked.
After few days my swap usage becomes 50% and bigger and bigger. System becomes slow.
to find cpu usage i just use htop.

The question is how do I find which program uses swap memory ?
How do I find program which leaks memory ?

I would just sort them by amount of memory they are using, just because a program is being swapped doesn't mean it's the program that's hogging all the ram up.

---

### Post by H4F on 2009-07-19
> **LightningCrash said:**
> /proc/$PID/status

Look at VmLock

can't find VmLock

---

### Post by H4F on 2009-07-19
> **jerome1232 said:**
> I would just sort them by amount of memory they are using, just because a program is being swapped doesn't mean it's the program that's hogging all the ram up.

Yeap but I need to know which programm and how much uses swap

---

### Post by LightningCrash on 2009-07-19
> **H4F said:**
> can't find VmLock

err VmLck

ie, my FF PID is 8121

lc@laptop:/proc/8121$ cat status|grep Vm
VmPeak:   473244 kB
VmSize:   397768 kB
VmLck:         0 kB
VmHWM:    223232 kB
VmRSS:    162540 kB
VmData:   346948 kB
VmStk:       224 kB
VmExe:        56 kB
VmLib:     35896 kB
VmPTE:       372 kB


VmLck is the swap used, effectively.

---

### Post by H4F on 2009-07-20
> **LightningCrash said:**
> err VmLck

ie, my FF PID is 8121

lc@laptop:/proc/8121$ cat status|grep Vm
VmPeak:   473244 kB
VmSize:   397768 kB
VmLck:         0 kB
VmHWM:    223232 kB
VmRSS:    162540 kB
VmData:   346948 kB
VmStk:       224 kB
VmExe:        56 kB
VmLib:     35896 kB
VmPTE:       372 kB


VmLck is the swap used, effectively.

Thanks. that really show swap usage

About htop
F2-colums-Available columns- there are plenty of options to display.
some of them
VSIZE
NSWAP
M_SIZE
M_RESIDENT
etc.
I could not find descriptions of those thinks in manual pages of htop.
does any one know what do they mean exactly ?
where to find all descriptions?

---

### Post by roccivic on 2009-07-20
Read top manual:
```
man top > /tmp/top; gedit /tmp/top; rm /tmp/top
```

---

### Post by p0cky84 on 2009-07-20
> **CREEPING DEATH said:**
> In the GUI:
System --> Administration --> System Monitor
BUT, that only shows the stuff in X.
In the CLI:
```
top
```CD
**Idiot.**

---

### Post by H4F on 2009-07-21
/proc# cat */status | grep VmLck
I get a list of VmLck which all are equals to 0 .
But my swap usage in that time ~256 mb 
so what's eating my swap then ?

---

