---
title: "Cron command: runs from CLI, but not auto?"
date: 2010-03-10
forum: General Help
---

### Post by pwebguy on 2010-03-10
I have a script that is basically a series of rsync commands called bkup_all.sh. This script is located in the /root/ dir.

From the command line (su'd as root), I can run the script like this:

/root/bkup_all.sh > /var/log/bkup/bkup_$(date +%Y%m%d).log

This excecutes perfectly, and all the rsync adn script output is saved in a log file in the intended destination. However, I want this command to run automatically, so again, su'd as root I enter:

crontab -e

then enter the following:

00 02 * * * /root/bkup_all.sh > /var/log/bkup/bkup_$(date +%Y%m%d).log

I want the script to run each night at 2:00am.

But, the script does not run. There is no log file generated and I do not see anything in the syslog or system messages to indicate an error.

Can anyone spot the problem, or tell me where to look for more info?

---

### Post by Brandon Williams on 2010-03-10
I think the '%' signs have special meaning in the crontab. Change each '%' to "\%" and see if that solves the problem.

---

### Post by pwebguy on 2010-03-10
That was it! thanks a lot!

---

