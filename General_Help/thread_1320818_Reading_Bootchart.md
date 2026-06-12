---
title: "Reading Bootchart?"
date: 2009-11-09
forum: General Help
---

### Post by doas777 on 2009-11-09
so I am disappointed with boot time on one of my PCs after the karmic upgrade (seems about 35 seconds slower than jaunty was), and I installed bootchart to try to determine what the cause of the issue is. 

I'm having a bit of trouble interpreting the output however. for instance, the time listed at the top does not seem to have any relationship to the amount of time the user experiences booting, so I'm unclear what it is trying to tell me. 

I also notice many very long bars, that have almost no processing or IO associated with them. are they "slowing" boot? 

am I just looking for processes that are bright blue or pink in places?

if anyone knows, or can point me to decent documentation (I've been looking, but no joy), I would be most appreciative.

Thanks

---

### Post by wildweathel on 2009-11-09
Bootchart is a little tricky.  First, Karmic measures boot time differently from Jaunty, from boot to 45 seconds *after* the login screen appears.  So, a Karmic boot time that's 45 seconds longer than Jaunty is actually the same, and one that's 35 seconds longer according to bootchart is actually a little faster.

For the rest of it it's better I *show* rather than tell.  Hold on a bit, and I'll run mine.

---

### Post by doas777 on 2009-11-09
ok that would be most kewl. Thanks.

you've already answered one of my questions: that the monitoring continues even after "boot" has completed, and that the statistic at the top is not my "boot time", but the duration of the monitoring session. very useful information.

---

