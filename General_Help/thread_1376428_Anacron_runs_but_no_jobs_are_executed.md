---
title: "Anacron runs but no jobs are executed"
date: 2010-01-09
forum: General Help
---

### Post by kempy1000 on 2010-01-09
I have been trying to setup anacron.

I have installed it and this is the contents of /etc/anacrontab
```

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly


```

Everyday i turn the machine on and the jobs in /etc/cron.daily dont get executed? But i check the contents of /var/spool/anacron/cron.daily and todays date is there.

I excecute:
```

sudo nice run-parts --report /etc/cron.daily

```

And the terminal just hangs for hours.

Thanks
Chris

---

