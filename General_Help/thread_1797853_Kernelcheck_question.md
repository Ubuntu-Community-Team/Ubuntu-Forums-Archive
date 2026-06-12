---
title: "Kernelcheck question"
date: 2011-07-05
forum: General Help
---

### Post by Z06Gal on 2011-07-05
Under custom installation, the last thing to mark is "number of jobs to send to the cpu."  Can someone tell me what that means?  Thanks in advance. :)


Robin

---

### Post by vivek.pandey on 2011-07-05
can you please paste the link which you are following to custom install your kernel?

---

### Post by Z06Gal on 2011-07-05
[http://tronprog.blogspot.com/2011/01/compile-linux-kernel-in-ubuntu-with.html](http://tronprog.blogspot.com/2011/01/compile-linux-kernel-in-ubuntu-with.html)

---

### Post by master_kernel on 2011-07-24
The number of concurrent jobs sent to the CPU for compiling.  Pretty much splitting up the job so that each processor core (many are dual-core or more these days) gets some work to do.  It speeds up the process.

---

