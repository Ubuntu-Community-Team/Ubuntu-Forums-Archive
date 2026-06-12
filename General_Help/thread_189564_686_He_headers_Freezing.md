---
title: "686 He headers Freezing"
date: 2006-06-05
forum: General Help
---

### Post by dejay703 on 2006-06-05
I have a Sony Vaio PCG-GRT100 (P4 w/out HT).  I am completely new to linux, and was reading a program's installation instructions.  It said that I needed to upgrade my headers.

I downloaded the 686 headers and another 686 file and installed them.  The next time I restarted, I think my computer was still using 386 ("$uname -r" returned 386).  Every time I restarted after this, my computer would freeze.  The first couple times, when I logged in, it would flash a black logon screen, and then go back to the GUI logon screen.  This would happen a few times, and then after that, one login would just freeze (the mouse could not move, the panels didn't finish loading, and the startup sound stopped in the middle).

I fixed this by changing the session that i logon to (hitting F10).  Instead of doing "Last Session", I did the default Gnome session.  After I could actually login, I completely removed the 686 stuff, and now it's working fine.  Does anyone know what's going on here?  THanks!

---

