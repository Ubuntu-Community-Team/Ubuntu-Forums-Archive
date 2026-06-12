---
title: "Consistent 80-90% CPU load"
date: 2006-05-25
forum: General Help
---

### Post by Progressive on 2006-05-25
I know about 20 of that is from my superkaramba system monitor theme itself.  However, where is the other 60 coming from?

I looked in KDE System Guard and everything looks fine.  I then rebooted and tried memory test mode or whatever, and it booted to root console.  I did a 'startx' and i checked my CPU Load, it was at near 0%

How can i figure out what is causing this?  I know it isn't a kernel problem.

One irregularity I found was that there was about 30-40 Kio_http processes running, presumably from Konqueror.  I closed them all and it didnt help one bit.

Please help me

---

### Post by codejunkie on 2006-05-25
[QUOTE=Progressive]I know about 20 of that is from my superkaramba system monitor theme itself.  However, where is the other 60 coming from?

I looked in KDE System Guard and everything looks fine.  I then rebooted and tried memory test mode or whatever, and it booted to root console.  I did a 'startx' and i checked my CPU Load, it was at near 0%

How can i figure out what is causing this?  I know it isn't a kernel problem.

One irregularity I found was that there was about 30-40 Kio_http processes running, presumably from Konqueror.  I closed them all and it didnt help one bit.

Please help me[/QUOTE]
have you tried running ```
top
``` in konsole it seems to do a better job of finding the process using so much cpu, at least it works better for me than ksysguard or gnome-system-monitor.

---

### Post by Progressive on 2006-05-25
I just tried top... it said i am only running about 20-30 percent CPU, assuming I read it correctly.

Nothing looked out of place there either.  Why is my superkaramba theme displaying the wrong information... but only on this user, not on root?

---

### Post by barbarian on 2006-05-25
hi,

try this:

*ps aux | sort -n +2 | tail -1*

then use *kill*.

---

### Post by zxcv70 on 2006-05-26
Have you recently updated kernel?.. I'm asking because I had the same or similar problem, always 80-90% CPU... it was HOT! than I've found an info that kernels for i686 make some truble, so I switched to kernel for i386 and it helped and it works :) now it's 2-3%.

---

