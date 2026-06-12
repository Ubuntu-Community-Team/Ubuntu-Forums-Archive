---
title: "thread synchronization"
date: 2010-03-20
forum: General Help
---

### Post by andradx on 2010-03-20
Hi everyone,



I'm implementing a multithreaded application in which it is required that all threads reach the same state of execution and then concurrently execute their instructions. I guess that while the threads handle no shared data, the execution flow should be nicely handled by the OS, without me needing to schedule the threads apart from a barrier at a certain stage.


Thing is, programming with Posix threads I haven't got the slightest clue of how such a thing is done. I have a version programed in OMP, which provides a more transparent way of sychronizing the threads with a barrier with a simple call to the directive #pragma omp barrier. But it seems that handling CUDA devices and contexts is commonly done using the pthread library.

Any help? Thanks,

Andradx

---

### Post by rnerwein on 2010-03-20
hi
you can do that in differen ways. for example you can use mutexes.
pthread_mutex_t mutex;
in main
pthread_mutex_init (&mutex, NULL);
pthread_create (&p1, NULL, print_minus, NULL);
.....
pthread_join (p1, NULL);
...
}
pthread_mutex_lock (&mutex);
action ...
...
pthread_mutex_unlock (&mutex);

have a look at the manual pages to
ciao

---

