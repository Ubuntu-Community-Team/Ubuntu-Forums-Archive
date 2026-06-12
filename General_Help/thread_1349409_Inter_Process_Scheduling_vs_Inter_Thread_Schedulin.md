---
title: "Inter Process Scheduling vs Inter Thread Scheduling"
date: 2009-12-08
forum: General Help
---

### Post by DeaducK on 2009-12-08
Hi

I was interested in knowing if the scheduling for CPU time between multiple processes was the same as the scheduling for CPU time between multiple threads of the same process. 

To be more precise, if there are p processes running, each running t number of threads, when the scheduler decides which thread gets the CPU next does it take into consideration that another thread from the same process just had the CPU? i.e, does the scheduler try to give preferences to threads from processes that didn't recently get the CPU. 

Also is that the same for most of the popular Linux distributions?

Thanks

---

