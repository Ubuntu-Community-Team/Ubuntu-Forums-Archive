---
title: "multiple ***glibc detected*** warnings"
date: 2011-06-03
forum: General Help
---

### Post by nataliest on 2011-06-03
Hi,

I've been running a script developed by someone else (downloaded from [http://code.google.com/p/force-distribution-analysis/](http://code.google.com/p/force-distribution-analysis/)).  Everything had been fine - however, when I ran one of the commands (g_fdatools) I originally got the following error ...

writing matrix frame 55*** glibc detected *** g_fdatools: double free or corruption (!prev): 0x00000000022ef590 ***

I looked through the forums and a lot of places mentioned using the " export MALLOC_CHECK_ = 0" to prevent this error from crashing the system.  When I did this, it still crashed, this time with a segmentation fault (no other information given).  

I figured I should go back and work through the original problem rather than just tell it to ignore so I changed MALLOC_CHECK back to 3 but the glibc error had changed to ...

*** glibc detected *** free(): invalid pointer ***

After searching and finding nothing I could really use I gave up, closed everything and went home.  Coming in this morning the error message has returned to the original 'glibc detected double free or corruption' error.  

Can anyone shed light on this for me.  I'm pretty new to linux and am getting a little more than confused with the problem.

Thanks
Natalie

---

