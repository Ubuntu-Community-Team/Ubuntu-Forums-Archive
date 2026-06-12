---
title: "sudden problems with mutex locks in C++ and Python with Ubuntu 8.04"
date: 2009-06-26
forum: General Help
---

### Post by fox@macalester.edu on 2009-06-26
Hi, there,

I have a Dell Latitude D630 running Ubuntu 8.04.  I have been keeping up with recent updates.  Suddenly, today, two previously working programs developed problems.  One program is in C++ and uses pthread to implement a couple of threads, and the threads share a mutex lock.  This worked well up until today, and today one of the threads started to starve, and was having to wait forever to aquire a lock.  The other thread was acquiring and releasing the lock multiple times, while the first was waiting.  The second program is in Python, and uses the threading module, including its simple lock object.  Also today, code that worked yesterday suddenly developed a problem where one thread was starving: the exact same behavior... a thread would wait for a lock, and never get it, even when the other thread acquired and released it repeatedly.

I am wondering if anyone else has seen this phenomenon, or has any suggestions for ways to further diagnose or fix the problem...   I am also wondering if there is a way to investigate the recent updates I installed to see if one of them was the culprit?

Thanks,

Susan

---

