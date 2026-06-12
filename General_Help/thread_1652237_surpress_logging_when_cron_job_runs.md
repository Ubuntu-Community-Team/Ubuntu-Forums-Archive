---
title: "surpress logging when cron job runs"
date: 2010-12-24
forum: General Help
---

### Post by graysky on 2010-12-24
I have a cron job that I'm running once per minute.  I don't want to have the /var/log/crond.log get updated 60 times per hour.  How can I suppress the logging of the job?

I've tried adding the following to the cron line but they just get logged right along with it!

```

*/1 * * * *     /path/to/script > /dev/null
or
*/1 * * * *     /path/to/script > /dev/null 2>&1
```

---

### Post by dcstar on 2010-12-25
> **graysky said:**
> I have a cron job that I'm running once per minute.  I don't want to have the /var/log/crond.log get updated 60 times per hour.  How can I suppress the logging of the job?

I've tried adding the following to the cron line but they just get logged right along with it!

```

*/1 * * * *     /path/to/script > /dev/null
or
*/1 * * * *     /path/to/script > /dev/null 2>&1
```

Gee that thing called Google is handy:

[http://www.linuxquestions.org/questions/linux-general-1/disable-cron-from-logging-to-syslog-653876/](http://www.linuxquestions.org/questions/linux-general-1/disable-cron-from-logging-to-syslog-653876/)

---

