---
title: "Hyperthreading DECREASES performance???"
date: 2009-10-28
forum: General Help
---

### Post by ichudov on 2009-10-28
At work, we have some users who ru a multithreaded app, and they need
every single bit of performance we can squeeze from computers.

We are looking into whether we can obtain additional speed performance
from using Intel hyperthreading, as opposed to disabling
hyperthreading.

If we are able to get benefits from hyperthreading, it will be a huge
argument towards converting certain high end users desktops to Linux
from Windows XP.

I wrote a test perl script, that starts several tasks in parallel. All
these tasks perform a certain amount of calculations and exit. The
test completes when all of them exit.
The results were actually a disappointment, if the number of tasks was
equal to the number of physical cores. For the test with four parallel
subprocesses, on four CPUs, It takes longer to run it with HT than
without HT.

I think that I understand why.

What I found is that not all of these parallel tasks finish at the
same time. This happens because often times, two tasks are assigned to
two logical CPUs that share the same core, and some tasks are assigned
to only one core, whereas some cores are idling.

I cannot believe that I am the only guy with this problem, and hope
that the Linux community has found a solution. For example, perhaps
they can assign higher priority to some logical CPUs (say, to 0, 2, 4,
6) and lower priority to others. This way the higher priority ones
would be filled with tunning tasks, before fake "shadow processors"
1,3,5,7 are utilized.

I would like to know if perhaps there is a boot option to this effect.

This is Ubuntu Hardy, 2.6.24 kernel.

I did try 2.6.31 kernel with the same result.

This article from Intel: 

    [http://software.intel.com/sites/oss/pdfs/mclinux.pdf](http://software.intel.com/sites/oss/pdfs/mclinux.pdf)

Talks about intelligent handling of multiple cores as a done deal, but in my experience that did not actually occur.

Thanks

---

