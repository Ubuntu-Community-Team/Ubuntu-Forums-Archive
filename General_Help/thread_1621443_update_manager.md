---
title: "update manager"
date: 2010-11-14
forum: General Help
---

### Post by wattssr148 on 2010-11-14
is there a way to set the time of day that the download will start?  I would like for the update manager to do all its downloads at about 3 AM every day. or on days that I want. How can I do this?
Thanks 
Wattssr148:confused:

---

### Post by azertyh on 2010-11-14
hello,
perhaps with crontab : [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
and sudo apt-get update && sudo apt-get upgrade

---

### Post by Belathor on 2010-11-14
There is also [cron-apt]("http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html") in the repositories.  According to that link, it defaults to updating the sources list and downloading the packages without installing, all you have to do is edit ```
/etc/cron.d/cron-apt
``` to specify when.  According to that link,
```

0 3 * * * root test -x /usr/sbin/cron-apt && /usr/sbin/cron-apt

```
should do what I think you want.  Here is the [Ubuntu Wiki page]("https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo") on how to update regularly.

---

### Post by wattssr148 on 2010-11-15
Thank you for all your help so far. I have gone with gome schedule but what I do not know is what to put in the command line for the update manager to run. I figure it will be a sudo command but what is the complete command? Thanks again for all you help.
Grandpa once told me the only stupid question is the one you already know the answer to.

---

