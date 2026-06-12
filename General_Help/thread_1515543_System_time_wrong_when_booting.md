---
title: "System time wrong when booting"
date: 2010-06-22
forum: General Help
---

### Post by armageddon1 on 2010-06-22
Hi,

In every fifth boot or so the computer thinks it's 2007 and therefore I am faced with some sort of shell instead of Gnome (paraphrasing: "the time does not agree with the last time the filesystem was mounted" or something like that). This is fixed by running fsck and pressing Ctrl+D. I want to get rid of this problem, but how?

> uname -a
Linux alpha-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 02:41:03 UTC 2010 x86_64 GNU/Linux

I am on a laptop, btw.

Cheers

---

### Post by gdonwallace on 2010-06-22
Generally this is caused by the CMOS battery needing to be replaced.

They are cheap and easy to do.  Just open up your machine, and it will be easy to find.  Looks like a large round silver disk.  Pull it out, find out what it is and replace it with the same thing.

The only downside is that your CMOS will need to be reconfigured.

Otherwise, I am not sure what could be causing the problem.  If it a newer machine, you may want to try the manufacturers website and see if there is anything they are reporting, or call them and find out if there is anything else that needs to be done.

Don't let them tell you its the OS, that would not cause this problem.

---

### Post by r_s on 2010-06-22
man hwclock would be the ideal place to start.

---

### Post by armageddon1 on 2010-06-22
A while ago someone at the ubuntu irc channel helped me tune in the correct time in hwclock, but that did not remove the problem. It could probably be the battery. Is there anyway to see this? When my laptop battery (not CMOS battery) was getting bad the computer would tell me that it might be either broken or old. Could I access such information for the CMOS battery?

---

