---
title: "FireFox 3B5 crashes"
date: 2009-09-03
forum: General Help
---

### Post by MX5EdL on 2009-09-03
Greetings:

Been running Ubuntu 8.04 on a Dell for about 4 months with no problems.

In the last few days Firefox 3Beta5 has started crashing on certain web pages.  Not sure what has changed.

I ran Firefox in Terminal, the only message I got was "Segmentation Fault."


Any recommendations?

Thanks,

Ed

---

### Post by CatKiller on 2009-09-03
I can't help you with your particular problem, but why are you still using the beta? You have Internet access, since you're using Firefox, so there's no reason why you can't use the Update Manager to update Firefox to the released version of Firefox 3.0 at least.

---

### Post by MX5EdL on 2009-09-03
Good point.

Since it had been working up to now, didn't think about it.

I'll look into upgrading it.

Thanks,

Ed

---

### Post by lovinglinux on 2009-09-03
[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by tgalati4 on 2009-09-03
Firefox uses sqlite database to cache pages.  When the database gets corrupt, strange things happen.  Save your bookmarks and clear your cache.

You may also be experiencing the "fsync" bug.  There are some issues with database functions writing to disk in a syncronized fashion while the operating system is also doing the same.  This results in I/O delays and race conditions which also manifest as strange firefox behavior.

---

### Post by norm.h on 2009-09-04
> **MX5EdL said:**
> Greetings:

Been running Ubuntu 8.04 on a Dell for about 4 months with no problems.
In the last few days Firefox 3Beta5 has started crashing on certain web pages.  Not sure what has changed.
I ran Firefox in Terminal, the only message I got was "Segmentation Fault."
Any recommendations?
Thanks,Ed

I had the same problem and managed to get away from the beta version of Firefox, and got a full upgrade to Ubuntu version 8.10 into the bargain.
I enabled the "important" and "recommended" updates in Synaptic Manager "settings" - "repository" - " updates", and set Release Upgrades to "normal releases".
This immediately made the version upgrade available, which took about 3 hours to complete.
norm

---

