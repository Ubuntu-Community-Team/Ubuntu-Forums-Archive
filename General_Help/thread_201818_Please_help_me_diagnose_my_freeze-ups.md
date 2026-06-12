---
title: "Please help me diagnose my freeze-ups"
date: 2006-06-22
forum: General Help
---

### Post by nageeb on 2006-06-22
I'm running 6.06 on an IBM NetVista P4 2.4Ghz machine and every once in a while, it freezes up on me.  It's almost like everything just grinds to a halt.  Whatever i'm doing, my terminal sessions lock up and eventually the machine either a) catches up and lets me continue my work or b) freezes and emits a constant beep, as if i was holding a button down on my kb (which i'm not).

I had some similar problems with this before, but it turned out to be a power management problem.  I added the no acpi switch on boot-up and disabled the APM in my BIOS and it worked out fine.  There's just this last little bug that i described above that's making me wonder if my machine is maybe fried. 

The last time it froze up was about 45 mins ago.  I rebooted it, and checked my kern.log.  Frankly, i can't make heads or tails of anything in there, but it doesn't look too good.  Especially when i've got two-pages of log entries that occur on the exact same time, down to the second.  I figure that's when the computer crashed, so i'm hoping someone might be able to give me an idea as to what happened and what i can possibly do to avoid this happening again.

Quick summary:  My comptuer freezes up as if it runs out of resources.  
  IBM Netvista P4 2.4Ghz / 1G Ram
  Ubuntu 6.06 server install - no X11 installed.  
  Apache/MySQL/FTPD are installed.
 

thanks

---

### Post by mbeierl on 2006-06-22
The kernel log you attached simply shows a normal boot sequence.  The timestamp on the left (Jun 19 10:11:35) is when the kernel logger wrote the entry.  The actual time the event occurred is in square brackets [42949372.960000] and you can see that those numbers are changing.

Sorry I can't be of any more help than that.

---

