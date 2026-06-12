---
title: "Find cumulative CPU time for processes for an interval"
date: 2010-02-20
forum: General Help
---

### Post by SecretCode on 2010-02-20
OK, my forum search and web search abilities have come up with nothing. But this should be simple enough ...

I want to find the cumulative CPU time used by each process between two points (defined by the user, e.g. running a command or clicking a button).

A first stab at this would be running ```
ps -eo pid,cputime
``` 
at the beginning of the interval and at the end, then doing some arithmetic on the two sets of results. But this only shows whole seconds of cputime ... and what about processes that started and stopped during the interval?

Any advice?

---

### Post by SecretCode on 2010-02-21
Anyone?

---

