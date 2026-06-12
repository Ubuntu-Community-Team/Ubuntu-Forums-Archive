---
title: "Scheduling update manager time-of-day runtime"
date: 2010-04-07
forum: General Help
---

### Post by nicklogan on 2010-04-07
I've searched for ways to do this with cron and come up empty. I want to schedule the update manager downloads for the 2-7am hours to avoid being penalized by my satellite service provider for excessive downloads. No, I can't change providers as I live in a rural area where it's the only relatively high speed option. If I download at this time it's not counted against me.

---

### Post by dcstar on 2010-04-08
> **nicklogan said:**
> I've searched for ways to do this with cron and come up empty. I want to schedule the update manager downloads for the 2-7am hours to avoid being penalized by my satellite service provider for excessive downloads. No, I can't change providers as I live in a rural area where it's the only relatively high speed option. If I download at this time it's not counted against me.

In /etc/cron.daily there is a script called apt which does the updates (AFAIK).

If you **move** this script somewhere else, and then set up a root cron job to run this script at the times you want, then your problem may be solved.

---

### Post by nicklogan on 2010-04-08
According to [https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo), it looks like "sudo apt-get install cron-apt" will automatically cause updates to happen at 4 am by default. I'll give it a try.

---

### Post by tgalati4 on 2010-04-08
In /etc/apt are a bunch of configuration files.  You can configure apt to just download files to the apt cache and then you can install them any time you want.

This has the advantage of allowing you to pick and choose which updates to apply.

Otherwise, you may get an automatic update that breaks graphics and then you won't be able to boot.  By picking and choosing, you have more control over what upgrades occur when.

Regardless, the downloads can take place as scheduled by cron-apt.

---

### Post by dcstar on 2010-04-09
> **nicklogan said:**
> I've searched for ways to do this with cron and come up empty. I want to schedule the update manager downloads for the 2-7am hours to avoid being penalized by my satellite service provider for excessive downloads. No, I can't change providers as I live in a rural area where it's the only relatively high speed option. If I download at this time it's not counted against me.

Since the daily apt update check is in the **cron.daily** job, you can change when that runs in the **/etc/crontab** file.

Anacron will still run it after boot-up if it has not already been run on that particular day, but if you leave your machine running continuously it should respect the times set in that file.

That job only kicks off the apt check, if apt is configured for weekly updates then that will occur.

---

