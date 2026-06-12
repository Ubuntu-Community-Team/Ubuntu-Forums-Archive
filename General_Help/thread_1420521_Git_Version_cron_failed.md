---
title: "Git Version cron failed"
date: 2010-03-03
forum: General Help
---

### Post by arthurccube on 2010-03-03
Hi Guys,

I've done a cron job using crontab by root:
"crontab ~/cron.txt"


I checked the cron log
"less /var/log/cron"

my tasks are run successfully.

However, the following line return no results in my script:

echo "`sudo -u ftpuser git pull`" >> $LOG

My script called "deployit.sh"
It succeed if I log in root and run it in any folder.

**Is there any setting in my script for using git???**

---

