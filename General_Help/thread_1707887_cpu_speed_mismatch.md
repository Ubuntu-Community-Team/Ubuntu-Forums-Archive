---
title: "cpu speed mismatch?"
date: 2011-03-15
forum: General Help
---

### Post by bnut on 2011-03-15
Is this correct?  If not, how do I rectify?

~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU    ** [COLOR=Red]E7400  @ 2.80GHz[/COLOR]**
stepping        : 10
[COLOR=Red]**cpu MHz         : 1600.000**[/COLOR]
cache size      : 3072 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2




Linux server 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

---

### Post by flipper T on 2011-03-15
your cpu "scales" its performance / speed depending on demand.

this saves energy & u think increases the cpu's life

your terminal output is a snapshot taken at the time you ran the command... ie nothing to worry about

---

### Post by bnut on 2011-03-16
> **flipper t said:**
> nothing to worry about

ty!

---

### Post by antaios256 on 2011-03-16
if you can please mark threat as solved. using the tools at the top. this would help anyone who is 1 having the same issue and 2 willing to offer help to those that need it.

---

