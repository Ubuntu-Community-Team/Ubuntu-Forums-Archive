---
title: "how to schedule tasks to run say weekly?"
date: 2009-12-15
forum: General Help
---

### Post by andrewharvey on 2009-12-15
I find that KDE's task scheduler GUI for cron (systemsettings then Advanced tab then Task Scheduler) is really good, but I want to know how to do this,

How do I schedule tasks at intervals say weekly, daily, or monthly when my computer is sometimes on and sometimes off. With cron you can only (for example) do it weekly at say 11am Monday, but my computer may not be on then (and there is no time every week that it is always on) so that important task will never get done that week.

I could patch together a shell script that runs at startup and checks the week and some flag that is set when the program is run, but then it will fail if I leave my computer on for 3 weeks in a row. I could also tell cron say every 10 minutes to run a metascript that checks to see if a given script has been run this week or not, but really I want to develop something that is of enough quality to be accepted into debain's universe repo.

Anyone know of existing solutions or possible methods to write something to do what I want (ie. should it just be scripts that are called by cron to act as meta scripts? or would I need to write my own version of cron?).

---

### Post by revanb on 2009-12-15
Given your requirements of once a week and no specific time...My opinion is that you should schedule a script to run every hour (or smaller intervals if desired). This script should check a logfile and see if your task has run in the week, if not it should run it and write to the logfile that is has run it. That way it will run the task once a week even if you have it on for only 1 hour and it will not run it more than once a week.

I don't know if, by weekly, you mean calendar weeks. Otherwise you could only check if it has run in the last 7 days which I guess may be easier to program?

---

### Post by llamabr on 2009-12-15
I run a few things in cron, but also run them on boot, just to be sure it's done, in case the box has been off for a while.

So, for example, I get all my podcasts via cron at 7am daily.  but in case it's been off for the weekend, or whatever, i also add it to my boot process.  That way double kill, so I'm sure not to miss it.

And double doesn't hurt anything, since it won't get anything twice.  What exactly processes are you worried about?

---

### Post by dcstar on 2009-12-15
> **andrewharvey said:**
> I find that KDE's task scheduler GUI for cron (systemsettings then Advanced tab then Task Scheduler) is really good, but I want to know how to do this,

How do I schedule tasks at intervals say weekly, daily, or monthly when my computer is sometimes on and sometimes off.
.........

```
man anacron
```

It is installed as default.

---

### Post by revanb on 2009-12-15
dcstar has nailed it! That is exactly what you described...It's great to have all these tools available in Linux!

---

### Post by andrewharvey on 2009-12-15
> **dcstar said:**
> ```
man anacron
```It is installed as default.

thanks all. anacron. that will do the trick, and it appears that its anacron that manages the /etc/cron.[daily|weekly|monthly] directories. its a shame that KDE's GUI doesn't allow you to add to /etc/anacrontab though.

---

