---
title: "log file size?"
date: 2010-06-11
forum: General Help
---

### Post by Enthrall on 2010-06-11
Is there a max log file size or do they keep growing? the ones in /var/log?

would "max log size = X "work?

---

### Post by arrange on 2010-06-11
It depends on the specific log, but generally it's all done automatically by a *logrotate* cron job. If you want to change the behaviour, look at */etc/logrotate.conf* and */etc/logrotate.d/*. 

Usually there's a time limit (like remove an old log *daily*), not a size limit.

---

