---
title: "related to nanosecond time"
date: 2011-02-19
forum: General Help
---

### Post by begroup on 2011-02-19
Hello all,
We are new to ubuntu and linux kernel programming.
We were tracing the implementation of gettimeofday system call and found that it called do_gettimeofday kernel function. It implicitly called getnstimeofday function.
In gettimeofday function the microsecond value is returned by multiplying nanosecond value by thousand.
What we want to do is that call to gettimeofday function should return nano-second time instead of micro-second time. 
For this we planned to modify gettimeofday but this solution is not feasible as gettimeofdayis used by many processes simultaneously.
So what is the feasible solution???
Any guidance would be appreciated..

---

### Post by hakermania on 2011-02-19
This {maybe} is helpful: [http://ubuntuforums.org/showthread.php?t=1380305](http://ubuntuforums.org/showthread.php?t=1380305)

---

### Post by rnerwein on 2011-02-19
> **begroup said:**
> Hello all,
We are new to ubuntu and linux kernel programming.
We were tracing the implementation of gettimeofday system call and found that it called do_gettimeofday kernel function. It implicitly called getnstimeofday function.
In gettimeofday function the microsecond value is returned by multiplying nanosecond value by thousand.
What we want to do is that call to gettimeofday function should return nano-second time instead of micro-second time. 
For this we planned to modify gettimeofday but this solution is not feasible as gettimeofdayis used by many processes simultaneously.
So what is the feasible solution???
Any guidance would be appreciated..

high

have a look at "man utimensat"
but when you want to deal with nano seconds - for ever reason you want - have a look at 
man sched_setscheduler and sched_getscheduler.
but be very careful when running realtime programms on your box. if you get a loop in your program and
you have only a single cpu you habe to hit the rest knop :-)

ciao

---

