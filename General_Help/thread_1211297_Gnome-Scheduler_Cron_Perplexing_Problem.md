---
title: "Gnome-Scheduler Cron Perplexing Problem"
date: 2009-07-12
forum: General Help
---

### Post by measekite on 2009-07-12
**Situation:**
Using Jaunty I am backing up HOME to a USB external drive using grsync/rsync.  I have tested the backup using just grsync and it works fine.  I then placed the rsync commands in Gnome-Scheduler (aka CRON) scheduled to start at 1:am.

The backup did not work.  I checked syslog and saw an entry that the job ran.

The next morning after checking both syslog and the USB drive and seeing the new files missing I then brought up Gnome-Scheduler, selected the task and chose RUN TASK from the menu.  The job did run correctly and the new files were backed up to the USB drive.

[COLOR=Red]**Question:**[/COLOR]
Does anybody know why this is happening and how to solve the problem?  If the job begans automatically at 1:AM UI am perplexed that the backup did not occur when syslog says it did and then when running the task manually from the Gnome-Scheduler menu it works fine.  Is there some bug in scheduler?

---

### Post by ajgreeny on 2009-07-12
I think you will need to do this with a bash shell script file. If you do not understand what this means come back again and I will show you.  I use a similar shell script to run radio recording scripts with mplayer or streamripper, and the only way I could get it to work was as a shell script.

Apparently the cron command line is much less able than a full bash command line, so you need to run a shell script, ie the full bash command written into a simple program and run that.

The script would be something like
```
#!/bin/bash
rsync -options source destination
```in text editor, but save as backup.sh and make it executable.  Then set that to run at your chosen time in gnome-schedule.

---

### Post by measekite on 2009-07-14
> **ajgreeny said:**
> I think you will need to do this with a bash shell script file. If you do not understand what this means come back again and I will show you.  I use a similar shell script to run radio recording scripts with mplayer or streamripper, and the only way I could get it to work was as a shell script.

Apparently the cron command line is much less able than a full bash command line, so you need to run a shell script, ie the full bash command written into a simple program and run that.

The script would be something like
```
#!/bin/bash
rsync -options source destination
```in text editor, but save as backup.sh and make it executable.  Then set that to run at your chosen time in gnome-schedule.

 I think I do understand this but have a question.  Can you place multiple rsync lines in the script and have then executed in the order they appear?  Basically I have 6 different backupt jobs I would like to run beginning at 1:00AM and have them run consecutively.

---

