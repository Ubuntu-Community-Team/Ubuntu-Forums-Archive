---
title: "Problems with monthly backup cron job"
date: 2009-07-02
forum: General Help
---

### Post by ecosprog on 2009-07-02
I am using rsync and cron to do my incremental daily and weekly backups and then once a month the daily backups get compressed and saved as a monthly archive.

The daily and weekly backups work flawlessly but the monthly compressed archive gives the following error.

/bin/sh: Syntax error: end of file unexpected (expecting ")")

I have looked at the syntax and can´t see any problems. If I run the tar job from the command line it works without a problem, but it won´t work from cron. I´m running these jobs as root and the cron file is as follows.

## rsync backups
00 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Documents /mnt/DataStore01/rsync/daily
10 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Photos /mnt/DataStore01/rsync/daily
30 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Graphics /mnt/DataStore01/rsync/daily
35 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/ecosprog_solar /mnt/DataStore01/rsync/daily
00 08 * * 5 /usr/bin/rsync -av --delete /mnt/DataStore01/rsync/daily /mnt/DataStore01/rsync/weekly
30 11 2 * * /bin/tar -cvjf /mnt/DataStore01/rsync/monthly/monthly_$(date+%Y%m%d).tar.bz2 /mnt/DataStore01/rsync/daily/

Any help with this would be much appreciated. I´m beginning to tear out the little hair I have left.

---

### Post by ethoxyethaan on 2009-07-02
> **ecosprog said:**
> I am using rsync and cron to do my incremental daily and weekly backups and then once a month the daily backups get compressed and saved as a monthly archive.

The daily and weekly backups work flawlessly but the monthly compressed archive gives the following error.

/bin/sh: Syntax error: end of file unexpected (expecting ")")

I have looked at the syntax and can´t see any problems. If I run the tar job from the command line it works without a problem, but it won´t work from cron. I´m running these jobs as root and the cron file is as follows.

## rsync backups
00 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Documents /mnt/DataStore01/rsync/daily
10 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Photos /mnt/DataStore01/rsync/daily
30 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/Graphics /mnt/DataStore01/rsync/daily
35 07 * * * /usr/bin/rsync -av --delete /home/ecosprog/ecosprog_solar /mnt/DataStore01/rsync/daily
00 08 * * 5 /usr/bin/rsync -av --delete /mnt/DataStore01/rsync/daily /mnt/DataStore01/rsync/weekly
30 11 2 * * /bin/tar -cvjf /mnt/DataStore01/rsync/monthly/monthly_$(date+%Y%m%d).tar.bz2 /mnt/DataStore01/rsync/daily/

Any help with this would be much appreciated. I´m beginning to tear out the little hair I have left.
try using the absolute path for date

/bin/date

---

### Post by ecosprog on 2009-07-02
Thanks for the quick reply. 

That´s one I had not yet tried. I will try now and report back.

---

### Post by ecosprog on 2009-07-02
Just tried the the absolute path for date (/bin/date) and still no go.

Anybody got any other ideas? I´m sure I´m missing something really obvious here. Failing that, anyone got a scipt that works in cron for a compressed monthly backup?

---

### Post by ecosprog on 2009-07-03
C´mon someone out there must have another idea. I really need to get this working.

---

