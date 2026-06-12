---
title: "Cron job"
date: 2011-11-19
forum: General Help
---

### Post by asai on 2011-11-19
I want to create a cron job that runs every minute between 0700 and 1900 every day. I am not sure how this line should look like or if it is possible?

---

### Post by papibe on 2011-11-19
Hi asai.

Check this crontab [tutorial]("https://help.ubuntu.com/community/CronHowto"). I think you can accomplish that with something like this:
```
*/1 07-19 * * * /usr/bin/somedirectory/somecommand
```
Hope it helps.
Regards.

---

