---
title: "fcron/fcronq problems"
date: 2010-08-20
forum: General Help
---

### Post by Ralph L on 2010-08-20
I have been experimenting with fcron and fcronq (fcron gui) for scheduling my system backups.  Currently I am using gnome-schedule, but if my computer is off during the scheduled time, gnome-schedule won't run the backup, when the computer is restarted.  I would like it to run it just once on restart no matter how many backups were passed over.  I read about fcron/fcronq on the web and they seemed like the right thing to use so I installed them.  fcronq is a gui front end and I like guis, hence I used fcron rather than anacron (as I was earlier advised to use).  However, fcron/fcronq work only intermittently and some strange things happen.

1.  I first installed fcron from Synaptic.  To my knowledge no user named fcron was installed.  Because fcron/fcronq didn't work right and fcron installed by Synaptic was old, I installed the latest version (3.0.6) from the fcron website.  During the install I was asked if I wanted a user "fcron" installed.  I said no, but the install script aborted saying it was unable to fine user fcron.  So I went to Users and Groups and installed a user fcron with no password (I didn't know what to set it to).  I then noticed that somehow a user "cron" had been previously installed, but it had the word "null" above it--whatever null means.  My question is, for what does a job scheduler need to establish a user?  Apparently both cron and fcron need one, but it sure seems goofy to me.  And what is a "null" user and how does one establish it--I noticed the the null user "cron" had no files in /home?  Also, if the older version of fcron didn't need a user "fcron", why does the newer version need one.

2.  Fcronq was installed in my System Tools menu.  When I did a restart, it went away.  This happened consistently several times.  This was certainly surprising.  Anybody know what is happening?  

3.  I looked up the dependencies of gnome-schedule and I see that it requires anacron rather than cron.  If it uses anacron (which I have been told will run skipped over tasks), why can't I use gnome-schedule and not have to bother with fcron/fcronq?  I noticed that cron was installed on my system.  Maybe it is incompatible with anacron and causing the uninstall described above???

4.  Finally the problem I have been having with fcron/fcronq is that sometimes a scheduled task I create runs on schedule.  Sometimes when I create one, it won't run as scheduled.  And if I make a change to the schedule, sometime it will no longer run.  I am using "& 30 4 * * * ~/lbtest" in the fcronq schedule table.  lbtest is a script in my Home directory and runs fine, when I double click it, or run it from terminal.
Any suggestions?

I am running lucid on a Dell D610 laptop.

Thanks
Ralph

---

