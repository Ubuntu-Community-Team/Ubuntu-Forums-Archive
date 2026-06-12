---
title: "Crontab problem"
date: 2012-04-11
forum: General Help
---

### Post by eawz9999 on 2012-04-11
**Ubuntu Natty server**. My crontab (root) works fine and sends emails when something is wrong. However the _crontab –u snort_ stopped sending email notifications after one of the latest upgrades (I do not know which one).
The only crontab –u snort is oinkmaster updated daily. The system log shows the cron job (snort) been executed but there are no signs of errors or execution by the email agent (postfix) and I do not receive emails. I added a test job every 5 minutes but this does not work either. I added MAILTO= in the crontab with no results.
This has me **puzzled** since it was working fine until last week.
Any help would be greatly appreciated.
Thank you, Enrique

---

