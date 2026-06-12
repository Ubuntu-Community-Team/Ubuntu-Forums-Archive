---
title: "find out why a kernel panic occurred"
date: 2011-03-17
forum: General Help
---

### Post by kainalu on 2011-03-17
I experienced a kernel panic today at 4AM. The computer was sitting idle, with the screen off. The screen lit up to show me a kernel panic. Where should I start, in order to find out why?

---

### Post by JC Cheloven on 2011-03-17
In the menu system-administrarion there is an application called "system log viewer" or something similar (I don't have an english machine at hand right now, sorry). There you'll find an entry for kern.log, and kern.log.1 . Not sure if some more; maybe. Inside each, there are some dates listed. Choose the date of your crashed session, and search for errors towards the end, or at any place (there is a search function).

This should serve as your starting point.

---

### Post by tgalati4 on 2011-03-17
Check the log files in /var/log.  Look for timestamps near 4 AM.  It could have been a power glitch.  Do you have an UPS?

---

### Post by kainalu on 2011-04-07
As it turns out, the computer was failing. The problems kept occurring until I ran a HW Diag. MB had popped caps. Dead PC.

It just proves the simplest explanation is usually the right one.

Thanks Guys!

---

