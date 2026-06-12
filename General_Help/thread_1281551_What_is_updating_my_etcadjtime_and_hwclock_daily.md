---
title: "What is updating my /etc/adjtime and hwclock daily?"
date: 2009-10-03
forum: General Help
---

### Post by loonsailor on 2009-10-03
On one of my ubuntu boxes, the file /etc/adjtime is being updated automatically every day at 23:43.  I assume that this means that something is calling hwclock to update it, which is a good thing.  On my other two ubuntu boxes, it doesn't happen.  My question is, what is doing it?  I can't find a cron job for it.  Oddly, ntpd is running on the two boxes that DON'T update it, but not on the one that does.  

More importantly, I guess, how do I add the automatic update to the boxes that aren't doing it now?

Thanks!

---

### Post by StuartN on 2009-10-03
> **loonsailor said:**
> More importantly, I guess, how do I add the automatic update to the boxes that aren't doing it now?

Under System->Administration->Time and date, change the Configuration from Manual to Automatic. You need to supply your password to unlock the Time and date settings.

---

### Post by loonsailor on 2009-10-03
Thanks for the help.  I'll do that, but one of my systems is headless.  Is it in some config file?  Where?

---

### Post by loonsailor on 2009-10-04
I just had a look, and the time and date gui is something else entirely.  Setting it to auto starts ntpd, which keeps the system time in synch with an ntp server somewhere.  What I'm asking about is the hardware clock, which is set by hwclock.  Something is keeping it in sync with the system clock on one of my systems, but not on the others.

---

