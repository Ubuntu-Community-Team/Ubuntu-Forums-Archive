---
title: "Ubuntu doesn't shut down properly and subsequently boots at runlevel 2"
date: 2011-12-28
forum: General Help
---

### Post by wolfgang.rumpf on 2011-12-28
I have a Dell Optiplex 745 that was running just fine - recently it started *not* shutting down properly (it gets stuck on the Ubuntu shutdown screen and hangs there for as long as I let it).  When I power the machine off manually then, it (of course) boots up in runlevel 2 - which means that none of the web services for this server (apache2, etc) are enabled.  HELP!  What do I need to do to figure out why the system isn't shutting down properly anymore?

---

### Post by wolfgang.rumpf on 2012-01-13
Solved my own problem - I was running an app called SequenceServer and it didn't shut down properly; it was blocking the entire system from shutting down.  :)

---

### Post by oldfred on 2012-01-13
If system seems to hang on shutdown, it is best to force it down, not just turn off computer.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

