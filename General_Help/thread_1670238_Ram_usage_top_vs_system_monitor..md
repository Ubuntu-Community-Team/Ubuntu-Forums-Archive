---
title: "Ram usage: top vs system monitor."
date: 2011-01-18
forum: General Help
---

### Post by yerayenrique on 2011-01-18
Hi there,

I'm doubtful about my Ubuntu's ram usage, as I'm getting different values in top and System Monitor:

System monitor:
[[IMG]http://img811.imageshack.us/img811/7066/sysmonitor.png[/IMG]](http://img811.imageshack.us/i/sysmonitor.png/)

top:
[[IMG]http://img818.imageshack.us/img818/7351/topjf.png[/IMG]](http://img818.imageshack.us/i/topjf.png/)

Any ideas on what could be causing this? What should I trust, Sysmonitor or top?

Thanks in advance!

---

### Post by davidmohammed on 2011-01-18
I believe there is a subtle difference - system monitor is reporting the memory usage of all the processes that YOU are using.  Top is reporting the memory usage of all processes (You + root + anybody else logged in).

Trust Top is my recommendation.

---

### Post by efflandt on 2011-01-18
It would be easier to compare using **free** command in a terminal.

```
             total       used       free     shared    buffers     cached
Mem:       8121596     916492    7205104          0      48716     269324
-/+ buffers/cache:     **598452**    7523144
Swap:            0          0          0
```The amount "used" in top does not show what you actually need after deducting buffers and cache (which are dynamic and can be utilized for programs or data as needed).

590284 - 27440 - 259424 = 303520
and some things use binary based blocks of 1024 vs. decimal 1000

---

