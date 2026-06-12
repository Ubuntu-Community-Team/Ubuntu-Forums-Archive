---
title: "crontab -e?"
date: 2009-07-04
forum: General Help
---

### Post by Gorlist on 2009-07-04
Good day, quick question - whats the difference between making an entry into crontab -e compared to placing a script into cron.d/daily/week/etc directories?

where is crontab -e stored?

Best Regards,

---

### Post by mike2357 on 2009-07-04
The cron.daily, cron.weekly directories are for the anacron command.  crontab -e is for the cron command.  crontab -e stores its files in /var/spool/cron/crontabs, but it's best to use crontab -e (or crontab -r or crontab <cron_file>) rather than directly modifying the file.

cron runs a command a specified time, and if the machine is not running at that time, the command doesn't get run.  anacron does basically the same thing, but if the machine is down, it will run the command when the machine comes back up.

For more information . . .
man 5 crontab
man anacron

---

### Post by Gorlist on 2009-07-04
right understood, thanks for the reply mike.

---

### Post by andrew.46 on 2009-07-05
Hi Gorlist,

> **Gorlist said:**
> whats the difference between making an entry into crontab -e compared to placing a script into cron.d/daily/week/etc directories?

I see that mike2357 has pretty much answered your question but you might be interested to also read the following Ubuntu document:

CronHowto
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

which gives a nicely written overview of the subject as well as some specific examples.

All the best,

Andrew

---

### Post by Gorlist on 2009-07-05
excellent, thanks.

---

