---
title: "Name that app..."
date: 2010-07-16
forum: General Help
---

### Post by x-shaney-x on 2010-07-16
I was using an app for backups a year or so ago but I can't for the life of me remember what it was called or where to find it.
I'm hoping the following description might ring a bell with someone who can point me in the right direction:

This was a gnome/gtk2 app which ran in the system tray and I could access the preferences panel from the tray icon.
The preferences panel was a very simple thing with checkboxes for different files and directories so I could set which ones I wanted to backup.

Once set, the app would run ion the background and make INCREMENTAL backups to a user specified location at user specified times (day, week, month etc).
I'm sure it also could be set to watch folders for changes and immediately make backups as things changed, like a sync mode or something, but I may have got the last bit mixed up with something else.

I don't bother backing up my home directory anymore because it soon fills up with junk but this app was fantastic for automatically backing up certain configs and photos etc (if I have to do it manually I tend to forget) and because it was only backing up changed files it didn't grind the system to a crawl as it copied files.

Of course I could just write a script to do this but this app is a much nicer way of doing it.

So, any ideas?

---

### Post by sisco311 on 2010-07-16
sbackup?
[uhelp]community/BackupYourSystem/SimpleBackupSuite[/uhelp]

---

### Post by x-shaney-x on 2010-07-16
> **sisco311 said:**
> sbackup?
[uhelp]community/BackupYourSystem/SimpleBackupSuite[/uhelp]

YESSSSS!!

Looking at it again it seems I did confuse another app with it but this is certainly the one I was thinking of.

Many thanks.

---

### Post by mike555 on 2010-07-16
you might also want to look at "LuckyBackup" I think it works better .

---

### Post by x-shaney-x on 2010-07-16
I notice LuckyBackup is a KDE app and since I don't use any other KDE app I'm not keen on installing tons of other stuff just for that.

Having said that, sbackup doesn't seem to be backing up.

I ran it with sudo in a terminal to make sure and in the configuration I selected Backup now".
I have looked through the system processes and there is nothing matching the process announced in the configuration.
There is also no sign of any backup files in the destination directory :(

---

### Post by mike555 on 2010-07-16
Where did you see LuckyBackup as KDE ? it isn't and doesn't install a bunch of KDE stuff .

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)   or you can get it from package manager .

---

### Post by x-shaney-x on 2010-07-16
> **mike555 said:**
> Where did you see LuckyBackup as KDE ? it isn't and doesn't install a bunch of KDE stuff .

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)   or you can get it from package manager .

I have absolutely no idea why I thought it was a KDE app, must have gotten confused (again!).

I found luckybackup a little confusing but got there eventually and it did the job manually so I'm assuming the scheduled job will also be okay.

Thanks :)

---

### Post by mike555 on 2010-07-16
it will auto backup if you clicked the little button second from the right (schedule ) and set a day/time ..

---

### Post by x-shaney-x on 2010-07-16
What happens if the computer is off at the specified time?
Will it try as soon as the comp is turned on after that or keep trying at the same time every day?

---

### Post by mike555 on 2010-07-16
not sure , probably same time.
   though you can set the same job to work at different times each day , just set one for the morning and the same job for a different time later in day .

---

