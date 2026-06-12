---
title: "Limited cron subset on battery possible?"
date: 2009-09-01
forum: General Help
---

### Post by dumb_question on 2009-09-01
I would like to run a limited subset of cron jobs while on battery (basically my crontab file only) - is this something that can be done easily? Or should I be trying to find another solution?

On a related note, if I have a script that sleeps for 10 minutes, then wakes up and does stuff, repeat, is there any reason this is less efficient than using cron to do stuff every 10 minutes? I am wondering if it might just be easier to write a little "batcron" script that only deals with my crontab file, and only when on battery power.

Thanks

---

### Post by DaithiF on 2009-09-01
> I would like to run a limited subset of cron jobs while on battery (basically my crontab file only) - is this something that can be done easily? Or should I be trying to find another solution?
yes it is possible.  A couple of the cronjobs in /etc/cron.daily do this (ie. they check if on battery, and if so, they won't run):
see
```
/etc/cron.daily/mlocate
```
for an example

---

### Post by dumb_question on 2009-09-01
> **DaithiF said:**
> yes it is possible.  A couple of the cronjobs in /etc/cron.daily do this (ie. they check if on battery, and if so, they won't run):
see
```
/etc/cron.daily/mlocate
```
for an example

I think I have the reverse problem though - cron seems to be switched off when operating on battery, so none of the crontab stuff is ever called. I could try to cancel this behaviour (Ubuntu Jaunty), but then I would have to go through all the default things triggered by cron and make them contingent on battery status. What I want is to selectively turn it on (as opposed to selectively turning it off) if that makes sense...

---

### Post by DaithiF on 2009-09-01
interesting, i'm mainly on a desktop, so wasn't aware that cron jobs got turned off when on battery.  A bit of poking around I found:
```
/etc/acpi/battery.d/15-anacron.sh

```
which causes anacron to get turned off when switching to battery.  The job for turning back on is in:
```
/etc/acpi/ac.d/85-anacron.sh
```

Now anacron takes care of jobs in cron.daily | weekly | monthly, but NOT the jobs in cron.hourly (though there are no jobs in there in my default jaunty install).  Jobs in cron.hourly are run by cron itself (crond), which doesn't seem to get turned off in the event of power switching to battery (or at least not in any way I could find).

Similarly, since crond takes care of your own crontab, and /etc/crontab, then I would guess that jobs there *would* still continue to run under battery.  This is probably where you tell me that they don't :) but in that case its a case of trying to hunt down the job that disables crond rather than anacron.  Have you tried adding a job to your own crontab and seeing if it runs as scheduled even if you are on battery power?

---

### Post by dumb_question on 2009-09-01
> **DaithiF said:**
> interesting, i'm mainly on a desktop, so wasn't aware that cron jobs got turned off when on battery.  A bit of poking around I found:
```
/etc/acpi/battery.d/15-anacron.sh

```
which causes anacron to get turned off when switching to battery.  The job for turning back on is in:
```
/etc/acpi/ac.d/85-anacron.sh
```

Now anacron takes care of jobs in cron.daily | weekly | monthly, but NOT the jobs in cron.hourly (though there are no jobs in there in my default jaunty install).  Jobs in cron.hourly are run by cron itself (crond), which doesn't seem to get turned off in the event of power switching to battery (or at least not in any way I could find).

Similarly, since crond takes care of your own crontab, and /etc/crontab, then I would guess that jobs there *would* still continue to run under battery.  This is probably where you tell me that they don't :) but in that case its a case of trying to hunt down the job that disables crond rather than anacron.  Have you tried adding a job to your own crontab and seeing if it runs as scheduled even if you are on battery power?

hmmm.... I did not know that there were > 1 "cron"s - I assumed my problems were due to anacron going off but will have to do some more debugging now...

thanks!

---

### Post by dumb_question on 2009-09-03
Just to wrap up the thread, /etc/crontab is indeed being executed on schedule on my laptop, even on battery power.

Thanks!

---

