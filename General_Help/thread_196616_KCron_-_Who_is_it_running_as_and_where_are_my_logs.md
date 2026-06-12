---
title: "KCron - Who is it running as and where are my logs?"
date: 2006-06-14
forum: General Help
---

### Post by ewangr on 2006-06-14
An old System V Unix user who went Windows for a few years, and then came to Linux a few months ago as Ubuntu/Kubuntu Dapper was coming online.

I have a script that is designed to run ipcheck with the appropriate command line options to keep my dyndns domain pointing at my home machine.

I then went into KCron, and setup a task to run daily at the top of each hour. However, I didn't see any option to set what user the task would run as.

Saved the task, and KCron shows it as being scheduled, but the ipcheck.log file in my home directory and the one in the root directory (one or the other should be updating) don't show any runs. If I select "Run it Now" in KCron, it does run the script, and update the log file in my home directory.

Any idea what I'm doing wrong?

---

### Post by scxtt on 2006-06-14
i don't know much about KCron (KDE cron manager?) but if anacron is installed on a Kubuntu distro, you can use it ... you can either add entries in /etc/crontab (system-wide) or do a "crontab -e" as the user you want to run the crons as and edit that users crontab file ... anacron is running by default in gnome, i haven't used KDE in years (back in my Fedora days) ...

---

### Post by ewangr on 2006-06-15
Well, I can certainly start messing with crontabs directly if necessary. But I'd rather use the KDE KCron tool if possible since it's a little easier to make sure I'm setting up what I think I'm setting up with the GUI.

On the other hand, perhaps there aren't that many KDE users using KCron out there?

---

### Post by scxtt on 2006-06-16
it's not that hard to get a handle on - there's plenty of documentation on it ...

---

### Post by iwonder on 2008-03-20
Well, there is documentation, but it falls short of the obvious details.  For example, the questions were:
Who is it running as?
Where are my logs?

You'll find nothing in the helpcenter doc on kcron dealing with those questions. However, here's what I found so far:

Who is it running as?
The user who schedules a task will have their own crontab.  There is a system-wide crontab, but the best I can tell, is not really used with the GUI kcron, unless you manage to sudo within the scheduled task.

Where are my logs?
Great question, and certainly the missing GUI piece.  The only place I've found information is in the task owner's mailbox file - /var/mail/<username>

Outside of that I don't see anything, and the only information available is from failed tasks.  Nothing in the way of runtime information is available that I can see.

Now, if I'm in error then someone with more definitive information is surely welcome to correct me.  I find the terse information very frustrating, as a newbie. Pointing out the obvious in saying there is documentation doesn't help folks using the forums for accessing information to seek answers IMHO.

---

