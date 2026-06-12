---
title: "Can't unmount partition for repair"
date: 2011-01-04
forum: General Help
---

### Post by Kildyt on 2011-01-04
Hi!

After reboot I saw this communication:
> Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.
and I can't shutdown the system normally because it stops (live cd too).

Then I can't repair this partition because it is always busy.

I have on this partition important files.

Help please. Any idea?

---

### Post by ridgeland on 2011-01-04
I always keep a copy of [SystemRescueCD]("http://www.sysresccd.org/Main_Page") around.  It's a liveCD that lets you mount and use anything on the PC.

---

### Post by Kildyt on 2011-01-05
Issue is solved!
I use fsck for repair partition from slax distribution (thanks to *markush* from LinuxQuestions.org forum).

---

