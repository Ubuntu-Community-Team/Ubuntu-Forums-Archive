---
title: "Nautilus' strange boot behaviour"
date: 2009-11-28
forum: General Help
---

### Post by iris-n on 2009-11-28
Hi all,

As many here, I've installed bootchart to measure the boot time in karmic. The 11/11 updates fixed the boot time for me, measured in a stopwatch. But by bootchart, it is still slow.

Intrigued by that, I set off to investigate, and I think I've found the real culprit: nautilus. Examine attached bootchart. After 45s, I have CPU and disk idle for ~15 secs, and by that time my desktop is already useful, and I consider it done. But at 60s there's a lot of I/O, and CPU activity. The processes responsible for it are nautilus, nautilus, and gconfd-2.

I find it weird. Is anyone here knowledgeable enough about nautilus to explain me what is happening, and if there's a way to fix it?

---

