---
title: "No splash, panel, or desktop after login"
date: 2006-01-25
forum: General Help
---

### Post by accord on 2006-01-25
KDE was running nicely this afternoon, but then it suddenly froze. Cursor was still moving, but the desktop was unreponsive. I restarted X and GDM was fine. Logged in with my account, the screen displayed a color background but the splash didn't come up. 

I checked "ps aux" on another tty and most of the X processes were started: the DCOP thing, splash --someoptions, and Chinese input. But there was nothing on my X tty but the color background and my cursor.

Logging in to GNOME or Xfce also produces the same results: I could login (GDM is fine) but not get past the splash, hence no desktop or panels or anything.

I tried logging in with another account, and everything was fine! So it must be some configuration file in ~/ gone wrong.

Before it happened, I removed a few packages, mostly under kdepim. But due to the fact that another user could login just fine, I do not think it's a package problem.

Nothing particular in .xsession-errors compared with the successful login of the other user.

Any idea how I might solve this problem?

---

