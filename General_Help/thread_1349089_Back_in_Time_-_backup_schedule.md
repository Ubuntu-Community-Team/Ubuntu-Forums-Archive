---
title: "Back in Time - backup schedule"
date: 2009-12-07
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-12-07
I'm using Back in Time on my Kubuntu 9.10 laptop for backups. So far the app is doing what I want except one thing. That is how to schedule the backups.

I have it set to backup once a day. But that only comes up at midnight which is kinda inconvenient since I don't leave the laptop running during the night. Meaning, no backup will be done unless I start Back in Time manually.
Also, I don't want it to run every hour. I don't have the backup drive in the office and I actually really don't want to have an hourly backup. Besides the fact that a full backup actually take longer then an hour.

So, my question is, is there a way for me to set Back in Time to run automatically at a set time?
If not, is there a similar app that allows to do that?
And please don't suggest doing it myself with rsync or something. I looked into that multiple time but didn't understand that thing. So, I need a GUI app.


Also, can Back in Time (or any similar app for that matter) backup to a server over the network? I would have thought it might be able to do it but I couldn't get it to work. After all it might be my network setup.
But would be nice to have a confirmation whether it can or can'T do it.


Thanks in advance for any help.
L&G

---

### Post by C-- on 2009-12-08
Is there a CLI interface? If so, use cron. Create a bash script that runs the commands you want to perform the backup, then use the crontab command to edit a file in which you place the path to the script and the time you want it to run. You can place any number of entries in this file and each entry will execute at the time you specify.

_[http://en.wikipedia.org/wiki/Cron#crontab_syntax]("http://en.wikipedia.org/wiki/Cron#crontab_syntax")_ <-- link

The wiki page shows the syntax for this.

If you are having trouble using rsync (which you'd need for writing the backup script to use with cron if you can't use Back in Time) check out grsync, a GUI for rsync, to help you understand.

_[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)_.

---

### Post by Linux&amp;Gsus on 2009-12-08
Thanks C--
I'll look into that.

---

### Post by jolindbe on 2010-10-15
In case this is still an issue for anyone, consider downloading the latest version of Back in Time, where you can choose not only "Daily", but also on which hour of the day the backup should be taken.
Sorry for bumping, but this should at least make this "Solved".

---

### Post by Linux&amp;Gsus on 2010-10-16
Thanks, just downloaded the newest version. Seems like that is what I was looking for.

Though, it took me a while to understand why *Back In Time* didn't start anymore.
The package changed from "backintime-kde" to "backintime-kde**4**"

---

