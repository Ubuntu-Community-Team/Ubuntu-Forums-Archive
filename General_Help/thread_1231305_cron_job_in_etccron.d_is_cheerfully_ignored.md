---
title: "cron job in /etc/cron.d is cheerfully ignored"
date: 2009-08-04
forum: General Help
---

### Post by supremedalek on 2009-08-04
Let's say I create a cron job file that looks like this:

```
% cat /etc/cron.d/ping
*/05 * * * * echo "ping" >> /tmp/pong
%
```

If I drop ping in /etc/cron.d, what do I have to do to make it be loaded/run? restart /etc/init.d/cron? And, shouldn't crontab -l show the cronjobs associated with root?  This is ubuntu 9.04 if it matters.

---

### Post by dcstar on 2009-08-05
> **supremedalek said:**
> Let's say I create a cron job file that looks like this:

```
% cat /etc/cron.d/ping
*/05 * * * * echo "ping" >> /tmp/pong
%
```

If I drop ping in /etc/cron.d, what do I have to do to make it be loaded/run? restart /etc/init.d/cron? And, shouldn't crontab -l show the cronjobs associated with root?  This is ubuntu 9.04 if it matters.

Don't call script files the same name as existing commands.

---

