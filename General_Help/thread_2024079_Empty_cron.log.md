---
title: "Empty cron.log"
date: 2012-07-13
forum: General Help
---

### Post by Azdour on 2012-07-13
Hi,

So I uncommented the cron line in /etc/rsyslog.d/50-default.conf:

cron.*            -/var/log/cron.log

I then restarted cron and rsyslog but the cron.log remains empty even when I see CRON output in the syslog.

I've even rebooted the machine and the issue is still there.

---

### Post by Habitual on 2012-07-13
so, crons are running to completion? any local mail re:crons?

---

### Post by Azdour on 2012-07-13
Hi,

Lol, as I was reading your reply I figured out the issue. The cron file in /var/log had the wrong owner and group - root:root when it should have been syslog:adm

---

### Post by Habitual on 2012-07-13
+1 for fixing it yourself.

---

