---
title: "How to schedule tasks that survive restart"
date: 2010-08-16
forum: General Help
---

### Post by Ralph L on 2010-08-16
I am trying to use gnome-schedule to schedule my system backup.  I have a procedure file that asks if the backup disk is mounted and then calls luckybackup.  I can schedule the backup task to run daily or weekly (or some other period) with gnome-schedule.  If the task is scheduled for a time when my computer is asleep, upon re-awakening the passed over task will start executing within a minute or so.

However, if I happen to have the computer completely shutdown at the time the task is scheduled, the backup is skipped.  Unlike the situation when the computer is asleep, the backup that was scheduled when the computer was shutdown will not be initiated when the computer is restarted.  This often results in backups being skipped.

Is there some way I can get a scheduled task to initiate when it was passed over, because the computer was off.  In my opinion a task that was scheduled, say to run daily, and finds the computer was off for several days should run just once when the computer is restarted.

I would prefer a gui solution like gnome-schedule, but if I have to use the Terminal I will give it a try.

I am running Lucid on a Dell D610 laptop.

Any help appreciated.

Ralph

---

### Post by JKyleOKC on 2010-08-16
Investigate the "anacron" system utility, which was created specifically to deal with such situations. A default installation of Ubuntu will include anacron and its schedule information, most of which is in the /etc directory. You can add tasks to its schedule, to be run once a month, once a week, once a day, or once an hour. It's a bit complex to set up but once you have it set, it's fully automatic.

For the details, open a terminal and type "man anacron" to get the official manual displayed. Man pages are often more than a little bit confusing and full of geek-speak, so don't hesitate to ask questions here about any part of it you don't find comprehensible at first glance!

You might also search the forums here for "anacron" and find how-to threads already in existence and easier to use than the man pages...

---

### Post by Ralph L on 2010-08-17
Jim

I have been doing some googling and found fcronq ([http://code.google.com/p/fcronq/](http://code.google.com/p/fcronq/)).  It is a gui front end for fcron, which is touted as being the latest and best of the cron's.  I liked the sound of it, particularly because it is a gui.

Do you know anything about it--whether it works, whether the user must have admin privilege to use it?

Thanks

Ralph

---

### Post by JKyleOKC on 2010-08-17
I hadn't heard of this one before; the "cron" that's part of a default Xubuntu install does everything I need so I hadn't looked beyond it. I learned about "anacron" because the regular cron tasks run it first and I needed to find out what it was...

The original cron normally runs as root, so requires admin access to modify its schedules. However it can be scheduled to do things for individual users, although I don't know exactly how to do so...

---

