---
title: "Cron messages without cron installed ???"
date: 2012-06-21
forum: General Help
---

### Post by fmmarzoa on 2012-06-21
I am receiving a lot of cron messages -one for each half an hour- from my laptop Ubuntu box, the weird thing is that I have NOTHING on the crontab at all, neither on root or in my regular user.

The email messages has this subject:

Cron <root@durruti>   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

And this body:

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/sqlite.so' - /usr/lib/php5/20090626+lfs/sqlite.so: cannot open shared object file: No such file or directory in Unknown on line 0

The body is a well-known bug and it is a message error without practical effect, since sqlite works well regardless it. But thats not the point, as I told the question is WHY I am receiving those messages...

If I do a:

crontab -e

Both as root or as regular user, my crontab files appear both VOID, so...

:confused:

---

### Post by dcottingham on 2012-06-21
What do you have in /etc/cron.daily, /etc/cron.weekly, and /etc/cron.monthly?

---

### Post by fmmarzoa on 2012-06-21
> **dcottingham said:**
> What do you have in /etc/cron.daily, /etc/cron.weekly, and /etc/cron.monthly?

A lot of things X-D all of them installed by Ubuntu itself.

I have found the problem into /etc/cron.d/php5

Thanks a lot, you have been of great help :-)

---

