---
title: "KSysGuard showing non-existent processes"
date: 2012-10-07
forum: General Help
---

### Post by Stonecold1995 on 2012-10-07
If I leave the System Monitor (KSysGuard) open for too long, it begins to display in the Process Table processes that are no longer running.  For some reason, if I start a process, the entry may not disappear from the Process Table even when I close it.  I know they aren't zombie processes (at least, they're not marked as such).  They also don't respond to any signals, not SIGTERM or even SIGKILL.  Another reason I know they aren't just zombie processes is that they aren't detected with the "ps" command, so the problem is in System Monitor itself.  When I restart System Monitor, the leftover processes vanish.

How do I prevent System Monitor from doing this?

[[img]http://www.pictureshack.us/thumbs/57746_extra_processes.png[/img]](http://www.pictureshack.us/images/57746_extra_processes.png)

---

### Post by Stonecold1995 on 2012-10-16
bump

---

### Post by Stonecold1995 on 2012-10-31
bump?

---

