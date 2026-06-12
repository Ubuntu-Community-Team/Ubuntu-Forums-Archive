---
title: "crontab repeats several times per minute"
date: 2012-08-03
forum: General Help
---

### Post by hodgesse on 2012-08-03
Hi
I'm using Ubunut 12.04 and running a cron job.

Here is the coll1.sh file:

cd /home/erin/stuff/img

a=`date +%s`
b=${a}_4.jpg
wget -O $b -q "http://www.houstontranstar.org/snapshots/cctv/4017.jpg"

and here is the crontab file:

*/2 18-19 3 8 6 /home/erin/stuff/coll1.sh

It runs about 4 times per minutes and then skips about 9 minutes.

Any suggestions as to what I am doing wrong, please?

Thanks,
Erin

---

### Post by SeijiSensei on 2012-08-03
Which crontab file, /etc/crontab or a user-defined crontab in /var/spool/cron?  If the entry is in /etc/crontab, it needs a username between the time entries and the command to be run.

With these times:
```
*/2 18-19 3 8 6
```

the script should run every other minute between 6 and 8 pm on 8/3.  I don't know why the final 6 is there; that means Saturdays.

What schedule are you trying to set up here?

It's not really possible from a cron job to run several times a minute since the cron daemon only wakes up once each minute.  Something else is going on.

What do you see in the log files for this job?

---

