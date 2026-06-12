---
title: "cpu affinity for init"
date: 2009-08-09
forum: General Help
---

### Post by sherif12345 on 2009-08-09
Hi,

I have recently read this amazing article, [http://www.linuxjournal.com/article/6799](http://www.linuxjournal.com/article/6799) , about restricting all processes to one processor on a dual-core system by setting the cpu affinity of init at start time and then setting the cpu affinity of a real-time program to the other cpu to minimize execution time jitter.

The article mentions how we can modify the start-up script /etc/rc.sysinit to change the cpu affinity of init so that all processes forked from it inherit the same affinity. 

Since ubuntu uses the System V init process, which file would be the equivalent of /etc/rc.sysinit ?

Thanks in advance.

---

