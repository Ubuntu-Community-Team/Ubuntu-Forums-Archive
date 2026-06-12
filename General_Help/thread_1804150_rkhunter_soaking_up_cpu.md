---
title: "rkhunter soaking up cpu"
date: 2011-07-14
forum: General Help
---

### Post by JeffZZZ on 2011-07-14
Hello,

    rkhunter has been running alot lately.  I didn't put it in crontab.  here is my ls cron* list


/etc$ ls cron*
crontab

cron.d:
anacron  php5

cron.daily:
0anacron  aptitude          dpkg        mlocate
apache2   bsdmainutils      exim4-base  popularity-contest
apport    chkrootkit        logrotate   rkhunter
apt       desktop-profiles  man-db      standard

cron.hourly:

cron.monthly:
0anacron  standard

cron.weekly:
0anacron  apt-xapian-index  man-db  rkhunter



Is this normal looking crontab?  Was rkhunter installed in crontab when I installed the package?


thank you
Jeffzzz

---

