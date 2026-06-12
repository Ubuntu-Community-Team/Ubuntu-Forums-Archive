---
title: "Compute-hogging jobs on multicore?"
date: 2010-12-07
forum: General Help
---

### Post by nick_d on 2010-12-07
hi,
I have been running some experiments for uni, it's basically a CPU-bound single-threaded task, that doesn't use a big amount of virtual memory.  The strange thing is that the computer becomes very unresponsive (to the point that the mouse moves jerkily across the screen, an interrupt issue??) even though it's a 4-core CPU, I would have thought that 3 cores would be available for running the desktop?  In fact I was thinking of running my experiments 3x faster by running 3 at a time and ignoring any memory-contention effects, leaving 1 core for the desktop so I can keep programming, but I'm not really comfortable doing this until I understand why the desktop slows down, I have now nice'd the CPU job and things seem better (though it's a bit early to be certain) but I wouldn't have thought this would be necessary on a multicore??  Any ideas?
cheers, Nick
PS. Ubuntu 10.10 amd64

---

