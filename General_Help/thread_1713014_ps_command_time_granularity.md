---
title: "ps command time granularity"
date: 2011-03-23
forum: General Help
---

### Post by robq on 2011-03-23
Hey everyone,

I need to find out about the TIME granularity with the ps command on ubuntu.

I was running the ps command on Mac OS X and the TIME is down to the millisecond (ms) in hhh:ss.ms format but today I switched to Ubuntu 10.10 and the TIME format seems to be dd:mm:ss with no ms available.

Is there a way to get ms granularity with the ps command on ubuntu the way there is on OS X?

I see that the TIME granularity is ms on Ubuntu with top so I'm hoping it's easy enough to get it to display with ps command.

Cheers!


Rob.

---

### Post by tgalati4 on 2011-03-23
Both top and htop give milliseconds, but appears that ps is hardcoded to display time with seconds only (no milliseconds) in Ubuntu (and most likely all debian-based gnu utilities).

You could compare the source code between BSD and Ubuntu's ps and see/modify the time output.

---

