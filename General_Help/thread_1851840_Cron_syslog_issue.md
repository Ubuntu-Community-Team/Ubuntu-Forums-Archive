---
title: "Cron syslog issue"
date: 2011-09-29
forum: General Help
---

### Post by manjunath.nm89 on 2011-09-29
I have written a custom cron. This cron executes a rake task every 5 minutes. I also log the trace of this execution in a file locally on my server. The whole process seems to execute seamlessly every 5 minutes, but then it seems to log it in /var/log/syslog. I investigated on the syslog and found that system's critical errors, and other cron issues are logged in syslog. Has anybody faced this kind of an issue ?

---

