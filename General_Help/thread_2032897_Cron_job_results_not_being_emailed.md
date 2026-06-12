---
title: "Cron job results not being emailed"
date: 2012-07-24
forum: General Help
---

### Post by ArlieS on 2012-07-24
I have a fairly new Ubuntu 12.04 LTS system, purchased pre-installed with what's presumably a normal workstation installation. What I need is a combination of workstation and server functionality, so I began installing various server packages. In particular, I installed postfix. I then created and tested a script intended to backup my files from one disk to another with rsync. I put that into root's crontab, using crontab -e. And I intentionally left rsync's "verbose" mode enabled, as a fast check whether cron was running the script. 

This morning I had output from system jobs run from cron.daily, probably via anacron. It had been mailed to "nobody" rather than either "root" or the account I'd tried to configure as the recipient of root's mail, but it was there. [I _think_ I've now fixed the problem that led to the mail being sent to "nobody"]  But I had nothing from the daily job I'd put into the root crontab. 

When I checked, I found that the cron job _had_ _run_. The last modified times on some of the files on the backup-receiving disk were long after I'd tested the script manually.  So the problem is only that the output of cron jobs does not appear to be being mailed.

Any idea what I can do about this?

---

### Post by ArlieS on 2012-07-25
This problem fixed itself - i.e. the cron job ran again last night, and this time I have the output I expected. Either that or it's intermittent - output only gets sent sometimes.

---

