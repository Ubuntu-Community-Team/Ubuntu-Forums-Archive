---
title: "Set maximum user memory allocation"
date: 2009-07-23
forum: General Help
---

### Post by Jbloudg20 on 2009-07-23
I have a few multi-user servers in an academic laboratory. I am having a problem with some users maxing out the available RAM, causing such sever slowdowns the machine essentially crashes.

I would like to set a maximum limit on the amount of ram a user can utilize.

This morning I experimented with setting limits via /etc/security/limits.conf and using ulimit. Neither of them prevented my test program, a simple infinite loop of mallocs, from crashing the server.

How can I achieve this?

Thanks in advance.

---

### Post by Jbloudg20 on 2009-07-23
Nothing? Really?

---

### Post by Brandon Williams on 2009-07-24
Which ulimit setting did you try? You want ulimit -v (virtual memory).

If I set this limit to, for example, 16384KB, then I am reliably unable to allocate any more memory than that for a single process. 

The data segment limit will only impact how large your heap gets (I think), and you can get around it by allocating large enough blocks that mmap is required. The memory size limit only effects real memory size (or maybe memory that can't be swapped out?), which your loop of mallocs will not exhaust.

---

### Post by PapaGoose on 2009-09-09
I have a similar problem- I have an account that's going to be used for parallel computing, so I need the memory limit to be per *user* rather than per process. The account needs to be able to run 1 instance of Matlab using say, a maximum of 6GB of memory, or 4 instances of Matlab with the total combined usage not exceeding 6GB. I can't just set the limit to 6GB/4 because then it would take reconfiguring to run a single instance with a larger limit.

Any ideas?

---

