---
title: "Cron job to hibernate and awaken"
date: 2010-07-25
forum: General Help
---

### Post by glenncvance on 2010-07-25
Hi everyone - I've set up one previous cron job to shutdown my machine at 10 pm - 

```
0 22 * * * /sbin/shutdown -h now
```

But now I would rather hibernate the machine at 10pm and then have it awaken at 7am. I have very little experience in writing cron jobs (I found the one above online) so any help would be appreciated. I'm running Xubuntu with Karmic. Thanks.

---

### Post by glenncvance on 2010-07-25
After doing some reading it seems that I need to suspend the machine, not hibernate it. To resume from hibernation you have to hit the power button, and I just want cron to resume my session.

---

