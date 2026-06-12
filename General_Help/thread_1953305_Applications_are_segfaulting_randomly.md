---
title: "Applications are segfaulting randomly"
date: 2012-04-06
forum: General Help
---

### Post by Luc484 on 2012-04-06
Hi! It's been a couple of days since my Ubuntu system started to act quite weirdly. It seems that many applications are continuously crashing because of a segfault. Chromium doesn't stay up for 10 minutes, Qt Creator crashes many times during the day, Firefox segfaults every hour etc...

I've been looking these days for someone else with the same problem but I found only one other person. Anyone who can help me figure out why this is happening? Anyone else experiencing the same? Is this a known recent bug?

I tried to strace a crash of chromium but this is the last part of what I get:

...
gettimeofday({1333693265, 853252}, NULL) = 0
gettimeofday({1333693265, 853289}, NULL) = 0
gettimeofday({1333693265, 853326}, NULL) = 0
gettimeofday({1333693265, 853363}, NULL) = 0
gettimeofday({1333693265, 853399}, NULL) = 0
gettimeofday({1333693265, 853437}, NULL) = 0
gettimeofday({1333693265, 853560}, NULL) = 0
gettimeofday({1333693265, 853628}, NULL) = 0
gettimeofday({1333693265, 853666}, NULL) = 0
gettimeofday({1333693265, 853704}, NULL) = 0
gettimeofday({1333693265, 853741}, NULL) = 0
gettimeofday({1333693265, 853778}, NULL) = 0
gettimeofday({1333693265, 853815}, NULL) = 0
gettimeofday({1333693265, 853852}, NULL) = 0
gettimeofday({1333693265, 853889}, NULL) = 0
gettimeofday({1333693265, 853926}, NULL) = 0
gettimeofday({1333693265, 853963}, NULL) = 0
gettimeofday({1333693265, 854000}, NULL) = 0
gettimeofday({1333693265, 854037}, NULL) = 0
gettimeofday({1333693265, 854074}, NULL) = 0
gettimeofday({1333693265, 854111}, NULL) = 0
gettimeofday({1333693265, 854148}, NULL) = 0
gettimeofday({1333693265, 854185}, NULL) = 0
gettimeofday({1333693265, 854221}, NULL) = 0
gettimeofday({1333693265, 854276}, NULL) = 0
--- SIGPROF (Profiling timer expired) @ 0 (0) ---
gettimeofday({1333693265, 854337}, NULL) = 0
gettimeofday({1333693265, 854374}, NULL) = 0
gettimeofday({1333693265, 854411}, NULL) = 0
gettimeofday({1333693265, 854448}, NULL) = 0
gettimeofday({1333693265, 854484}, NULL) = 0
gettimeofday({1333693265, 854520}, NULL) = 0
gettimeofday({1333693265, 854554}, NULL) = 0
gettimeofday({1333693265, 854590}, NULL) = 0
gettimeofday({1333693265, 863505}, NULL) = 0
gettimeofday({1333693265, 863556}, NULL) = 0
gettimeofday({1333693265, 863595}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

I tried to run a memtest and no error was found.

Thanks!

---

### Post by mitomito on 2012-04-06
Might have something to do with kernel update. Boot to previous kernel and see if you still have the problem.

---

### Post by Luc484 on 2012-04-06
Yes, I've been working all the day with the previous kernel and no crash. Also, guys in #ubuntu-kernel confirmed the bug. Thanks.

---

