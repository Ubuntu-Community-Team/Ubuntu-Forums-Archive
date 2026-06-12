---
title: "Can't get my blasted cron/shutdown script to work"
date: 2010-06-18
forum: General Help
---

### Post by Kirbysuperstar on 2010-06-18
Hi all, I'm trying to get cron to start shutdown at 1700, but it never actually seems to launch.

The line I have in the root user's crontab is
```
0 17 * * * root /sbin/shutdown -h +5
```

(the user gets a five minute warning and a Zenity pop-up notifying them of this, which works fine under their own crontab)

ps aux doesn't show shutdown as running, though. I'm at a loss as to what could be going wrong. Any advice?

---

### Post by MichealH on 2010-06-18
Instead of inserting a root into the command try editing it with
```
crontab -e -u root
```
instead of just the -e.

---

### Post by Kirbysuperstar on 2010-06-20
> **MichealH said:**
> Instead of inserting a root into the command try editing it with
```
crontab -e -u root
```
instead of just the -e.

Ah, that worked. Or.. it did, once. Now it's back to not doing anything.

Are there any logfiles that cron writes to? I could possibly get a hint of what's going on from there.

---

