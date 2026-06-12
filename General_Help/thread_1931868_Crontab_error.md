---
title: "Crontab error"
date: 2012-02-26
forum: General Help
---

### Post by MikeFlint on 2012-02-26
So,the issue here is (and sorry to resurrect an old thread but just bit me so ...)

The user-level crontab entries run as that user;
System-level crontab's (e.g. /etc/cron.d  /etc/crontab) require an extra parameter prior to the command to set the user

So this error means that the user being specified is not known, which occurs if you take a user crontab and place it under /etc/cron.d (and fail to add a user name!) then the 'user' is mistakenly taken from the command.

---

### Post by oldos2er on 2012-02-26
Post moved to its own thread.

---

