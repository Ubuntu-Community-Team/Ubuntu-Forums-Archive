---
title: "Cron broken"
date: 2010-06-09
forum: General Help
---

### Post by yanewby on 2010-06-09
For a few days I have noticed that my scheduled tasks have not been running.  My system is a freshly installed Lucid installation (maybe a week old).  I have checked all my scheduled tasks can run from the command line (and they do run as expected).

I decided to add an item to my crontab that wrote the date/time to a file on my desktop every 2 minutes that the PC was running:

*/2 * * * * date >>/home/yanewby/Desktop/test-cron.txt

This never gets executed.

If I do "status cron" in terminal it states: cron stop/waiting

The only solution I have found to this problem and to get cron working until I restart again is to reinstall cron using this command:
sudo apt-get install --reinstall cron

How can I fix cron?  Where do I look for further troubleshooting of this problem, is there a log somewhere that might have some error messages?

---

### Post by hysterix` on 2010-07-15
Did you ever figure this out or do you now not use cron?

[http://www.google.com/search?q=lucid+cron+broken](http://www.google.com/search?q=lucid+cron+broken)

Apparently I'm not the only one.

---

