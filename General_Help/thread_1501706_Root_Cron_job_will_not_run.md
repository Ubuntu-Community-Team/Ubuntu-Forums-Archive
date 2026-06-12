---
title: "Root Cron job will not run"
date: 2010-06-04
forum: General Help
---

### Post by ub-newbie on 2010-06-04
OS= 10.04

Problem:  Cron job's I have created to run every hour as ROOT since upgrading to 10.04 will not run.

Indications:
```
sudo crontab -e
``` produces ```
0 * * * * hddtemp /dev/sda >> /30GB/temp_logs/hd-temp.log && exit # JOB_ID_4
0 * * * * hddtemp /dev/sdc >> /30GB/temp_logs/hdtemp-c.log && exit # JOB_ID_5

```

auth.log shows:
Jun  4 14:27:01 Ubuntu CRON[3886]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun  4 14:27:01 Ubuntu CRON[3886]: pam_unix(cron:session): session closed for user root

I can manually run the jobs and they perform as expected.

JOB_ID_1 is a shutdown that I created before upgrading to 10.04, and it runs as expected.

/etc/cron.hourly is empty (not sure is this is normal or not)


Any ideas?

---

### Post by gaussian on 2010-06-04
I think you need to give full path to the command for a cronjob (e.g. /usr/bin/hddtemp or /sbin/hddtemp).

---

### Post by ub-newbie on 2010-06-04
Gaussian,  Thanks for not says "just like the pop up window tells you to"..

Your advice fixed this problem. 

.

---

