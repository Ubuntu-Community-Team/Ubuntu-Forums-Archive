---
title: "After upgrading to 12.04, my CPU gets locked on  I/O load of 45+ after 12 hours."
date: 2012-05-11
forum: General Help
---

### Post by TrevorBradley on 2012-05-11
I'm getting really frustrated with this latest upgrade to 12.04.

I've been using ubuntu on this machine since the 10.10 beta, and apart from a few glitches everythings generally been OK.  Now my ubuntu life is a nightmare.

I had some severe NVIDIA problems which I may have managed to resolve with a driver upgrade.  However I seem to have a second problem seems to be non NVIDIA related.

If I boot the machine and leave no apps running on the desktop, switch to a terminal with Ctrl+Alt+F6 and leave top running, the cpu load average will gradually increase.  This morning I saw a load average of 45, with one zombie process and almost 100% of the CPU in the "wa" (I/O wait) state.  With the command console I could get basic diagnostic information, but if I attempted to kill processes (e.g. kill -9 compiz) the system would freeze.

To make things worse this is a software RAID system and doesn't take well to being rebooted.  It takes a good 16 hours with every reboot (even Alt+SysRq) to resync the drives which isn't helping my load average either.

I've rebooted again and the drives are resyncing and things seem relatively happy - no zombie proceess, near 0% wa CPU, but I know it's only a matter of time.

The processes that seem to be sucking up the most CPU are md2_raid/md2_resync, mythbackend and compiz.

I feel close to figuring this one out (at least I can see what I'm doing now!) but feel stumped as to where to check.  If I see a zombie process is it likely to be the one causing 100% I/O load, or have I got cause and effect reversed?  What are some diagnosing good rules of thumb if your system has massive I/O load?

---

