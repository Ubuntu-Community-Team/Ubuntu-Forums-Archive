---
title: "HP G60-120US Processor Scaling"
date: 2010-12-31
forum: General Help
---

### Post by raidersin2004 on 2010-12-31
Basic Info: Ubuntu 10.10, AMD RM-70 2GHZ Processor, HP G60-120US, Bios F54.

I'm unable to scale my processor (either core) using the applet in the menu bar. Every time I try, I select 2GHZ, and re-open; then it's displayed that 500MHZ was selected. I'm unable to pick any speed, the computer has a mind of it's own in that sense.

It's essentially stuck at 500MHZ for 98% of the uptime, which makes it impossible to do anything more than web browsing. Ex: I tried watching an HD video, I watched 5 min, and 1,400 out of the 10,000 or so were dropped!

Any Insight or Ideas?
Thanks,
Jason

---

### Post by dcstar on 2011-01-01
> **raidersin2004 said:**
> Basic Info: Ubuntu 10.10, AMD RM-70 2GHZ Processor, HP G60-120US, Bios F54.

I'm unable to scale my processor (either core) using the applet in the menu bar. Every time I try, I select 2GHZ, and re-open; then it's displayed that 500MHZ was selected. I'm unable to pick any speed, the computer has a mind of it's own in that sense.

It's essentially stuck at 500MHZ for 98% of the uptime, which makes it impossible to do anything more than web browsing. Ex: I tried watching an HD video, I watched 5 min, and 1,400 out of the 10,000 or so were dropped!

Any Insight or Ideas?
Thanks,
Jason

Look in the syslog for the scaling entries created on bootup, then you can look for any messages reporting problems etc.

---

