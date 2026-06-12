---
title: "Back In Time"
date: 2009-11-01
forum: General Help
---

### Post by Quarkrad on 2009-11-01
I have just downloaded and installed Back In Time - this looks a good simple utility to backup key folders to another drive on my PC.  I thought I would experiment by backing up my mozilla mail and firefox folders.  However, when I fired up Back in Time and navigated to my Home folder all I could see were the standard folders - I could not see  all the hidden folders.  Is there a way to view/select the hidden folders?

---

### Post by darco on 2009-11-01
After you choose the folders then the path to save, there is a green + button that you can use to "show hidden folders"...
I am running now to see if it actually backs it up...

darco

---

### Post by Roasted on 2009-11-01
Just to throw out another idea here in case your Back In Time situation doesn't do what you need, you could look into rsync to back your stuff up. I have a drive that mounts to /media/localbackup, and I run

rsync -a --progress --delete /home/jason/ /media/localbackup

And it throws all of my data on 'localbackup', even hidden folders and all.

Just toss the command in a script, chmod +x to it to be executable, throw it in crontab to run at a certain time and presto - automated data backup. Mine runs twice a day - 4 am and 4 pm.

Just a thought to get out there on the table. Hopefully back in time works for you!

---

### Post by Quarkrad on 2009-11-02
Roasted - thanks, this looks good for some other things I need.  Your comment **Just toss the command in a script, chmod +x to it to be executable **- as a newbie to Linux where can I go to learn more about these commands and making scripts/executables?  I keep reading/coming across chmod.

---

### Post by ElSlunko on 2009-11-02
By default back in time ignores hidden folders that begin with a ".". I believe this is the nature of it however I can't verify as my ubuntu machine is currently in use.

---

### Post by Roasted on 2009-11-03
> **Quarkrad said:**
> Roasted - thanks, this looks good for some other things I need.  Your comment **Just toss the command in a script, chmod +x to it to be executable **- as a newbie to Linux where can I go to learn more about these commands and making scripts/executables?  I keep reading/coming across chmod.

My bad, dude. I should have been more descriptive.

First, find a place you want to store your script. I store my backup script in /usr/local/bin. So, navigate to /usr/local/bin by doing "cd /usr/local/bin". Then, type sudo gedit backup. What this does is it will create a blank text file named backup and open an editor.

Then, add this to the first line. All bash scripts start with this:

#!/bin/bash

Then below it, add your rsync command.

My rsync command is:

rsync -a --progress --delete /home/jason/ /media/localbackup

rsync = remote synchronize
-a = archive mode (preserves permissions, group ownership, time stamps, etc)
--progress = if I run backup in terminal, it'll display what it's doing at the time
--delete = If it doesn't exist on source (/home/jason) but it exists on /media/localbackup, it'll delete it from /media/localbackup. This ensures to ME in MY situation that "localbackup" is as identical as possible to /home/jason.
/home/jason = source
/media/localbackup = destination (spare 500gb drive in my system)

So overall you have:

#!/bin/bash
rsync -a --progress --delete /home/jason/ /media/localbackup

Of course, your rsync command must be customized to YOU. This is just my command I use.

Save it, and close the file. Now, in terminal, you're still CD'ed into /usr/local/bin, where "backup" now resides. SO... type sudo chmod +x backup

This grands executable permission to "backup". Why do you want executable permission? So you can go to terminal, type "backup", and it executes. AKA - it runs.

Then you can edit crontab to make "backup" launch at certain times. I launch mine automatically at 4am and 4pm every day.

I cannot give you more information on crontab at this time because I'm at work stuck on an XP laptop (barf), but what I told you above is all from memory and that's all I can remember. Later I can help you with crontab, so I'll be sure to post back here then.

Quick synopsis of the above:

-Created bin/bash script.
-Added the actual command to script.
-Granted executable rights to script.

---

### Post by Barriehie on 2009-11-03
Crontab is really useful.  I've got all sorts of things going on in there.  Google will turn up all kinds of examples, etc.

Here's a section of mine:
```

#
# Delete logfiles older than 14 days @ 0130 hours
#
30 1 * * * root find /var/log -mtime +14 -iname *.gz -exec rm {} \;

#
#
#
# m h dom mon dow user	command
##################################################
#            Twice a week backup at 4:00 AM
#
#
0 4 * * 0 root /backmeup.sh 1>/home/barrie/Desktop/1.log 2>/home/barrie/Desktop/2.log
0 4 * * 3 root /backmeup.sh 1>/home/barrie/Desktop/1.log 2>/home/barrie/Desktop/2.log

0 5 * * 0 root chown barrie:barrie /home/barrie/Desktop/Backup.log
0 5 * * 3 root chown barrie:barrie /home/barrie/Desktop/Backup.log

#
#
#
###############################################
#	Update my blacklist(s)
#
#
0 2 * * 0 root /home/barrie/bin/blacklist-updater.sh 1>/home/barrie/Desktop/bl1.log 2>/home/barrie/Desktop/bl2.log

20,40 * * * * root dhclient

#
#
#
##################################################
#	Clean up FireFox's Sqlite Files 
#
#
30 3 * * 0 barrie /home/barrie/bin/ffclean.sh
30 3 * * 3 barrie /home/barrie/bin/ffclean.sh


```

Barrie

---

### Post by ubun_two on 2009-11-03
> **ElSlunko said:**
> By default back in time ignores hidden folders that begin with a ".". I believe this is the nature of it however I can't verify as my ubuntu machine is currently in use.

I think you are right.  This is to avoid backing up cache, I think.

I wanted to back-up mozilla directories, so I removed this rule.  I added cache directory to the blacklist though.

---

### Post by Quarkrad on 2009-11-08
Roasted - thanks; I followed your instructions and I have got it to work - brilliant.  As I use my PC all sorts of times I would really like to run this script (automatically) at shutdown.  I am playing with 'Scheduled Tasks' which I believe is based on cron but there is not a 'shutdown' option.   Any help on getting scripts to run on shutdown would be much appreciated.

---

### Post by Barriehie on 2009-11-08
> **Quarkrad said:**
> Roasted - thanks; I followed your instructions and I have got it to work - brilliant.  As I use my PC all sorts of times I would really like to run this script (automatically) at shutdown.  I am playing with 'Scheduled Tasks' which I believe is based on cron but there is not a 'shutdown' option.   Any help on getting scripts to run on shutdown would be much appreciated.

Been googling to no end and it seems that no matter how you choose to shutdown your machine all roads lead to the shutdown command which isn't nice about killing the running process'.  How about turning the problem around; make a script that runs your backup routine and then shuts down the computer.

```

#!/bin/bash
backuproutine.sh && shutdown -P now

```

Barrie

---

