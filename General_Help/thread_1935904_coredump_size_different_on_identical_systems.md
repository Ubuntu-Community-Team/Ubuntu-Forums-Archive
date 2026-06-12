---
title: "coredump size different on identical systems"
date: 2012-03-05
forum: General Help
---

### Post by rvoinea on 2012-03-05
Hi

I have the following puzzling problem...

I have two almost identical systems based on ubuntu 10.10. On these systems there is an application running. At some point the application crashes and gives a coredump. On one of the systems, the coredump is 23M on the other is 88M. 
Both systems run the same application and the coredump file size is set to 0 on the system but the application sets it to UNLIMITED.

My problem is... why is this HUGE difference in coredump size?

"/proc/PID/coredump_filter" are identical and so are "ulimit -a".

Any ideas?

---

### Post by rvoinea on 2012-03-07
Apparently the two systems have a slightly different config for the app that is crashing.

Switching configs from one system to another gives the expected result (~23M and ~88M).

---

