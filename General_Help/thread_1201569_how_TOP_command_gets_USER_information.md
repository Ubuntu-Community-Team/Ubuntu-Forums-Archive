---
title: "how TOP command gets USER information"
date: 2009-07-01
forum: General Help
---

### Post by dileep.kk on 2009-07-01
Hi all ,
when i type command top I got the message as follws
 
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
1 root 15 0 2100 720 624 S 0.0 0.1 0:01.06 init
2 root RT 0 0 0 0 S 0.0 0.0 0:00.00 migration/0
3 root 34 19 0 0 0 S 0.0 0.0 0:00.00 ksoftirqd/0
4 root 10 -5 0 0 0 S 0.0 0.0 0:00.04 events/0
5 root 18 -5 0 0 0 S 0.0 0.0 0:00.00 khelper
6 root 11 -5 0 0 0 S 0.0 0.0 0:00.00 kthread
9 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kblockd/0
 
I want to know how this top command getting USER information exactly.

---

### Post by upbeat.linux on 2009-07-01
```
man top
```

or

[http://www.manpagez.com/man/1/top/](http://www.manpagez.com/man/1/top/)

---

