---
title: "Copy/Backup Files"
date: 2009-09-22
forum: General Help
---

### Post by jaqian on 2009-09-22
Hi I have two drives one is called **WORKING** and the other is **BACKUP**.

I want to be able to run some program/script that will compare **W** & **B** and see that **B** is missing a file on **W** and copy it over. I don't want or need compression. The copy/backup will be over USB2.0.

I don't mind using commandline as long as its not too complicated but would prefer a gui program. Any suggestions lads?

Btw I'm running [COLOR="Green"]**Mint 7**[/COLOR].

Cheers,
Rob

---

### Post by akakingess on 2009-09-22
I am not the best source of info for this, but I have heard the rsync does an excellent job, and I believe that they have a gui version called grsync. You might want to give it a try, and see if it will do all that you need, or wait a little longer as more experienced people start to respond, this is just to get you started at looking at at least one option.  Sorry I couldn't be of more assistance.

Edit:  Also, after getting grsync to work, if it works for you, there are some simple chron jobs you can set up to backup it up at certain times and to run automatically, unless you really feel you need to backup after every change that you make.

---

### Post by stumbleUpon on 2009-09-22
Yes, rsync is the software you need and you do

rsync yourOptions sourceFolder destinationMachineIP:/destinationFolder

where yourOPtions is a lot of options that you will have to decide. See here for more info about using it and also the GUI version

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)


You can actually schedule a cron job that will automatically do the backup at a specified time. See here

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by frncz on 2009-09-22
Have you tried 'keep' ?

It works for me

Regards

Mike

---

### Post by jaqian on 2009-09-22
Thanks for all the replies.

One thing I want to ask (probably should have mentioned before) is will rsync or whatever give me a human readable file after copying? Reason I ask is that I tried out a WesternDigital backup program on my windows box and it backedup everything alright (I presume) but I wasn't able to view or understand what it was as seemed to be random bits & bytes if you can understand what I mean. If I've a jpeg on my WORKING drive I want to be able to view the same jpeg on my BACKUP drive.

I wonder would the "cp" command be better? What do you think?

Cheers,
Rob

---

### Post by XCan on 2009-09-22
Perhaps ```
 rsync -av /path/to/W /path/to/B > rsynclog.txt 
``` would do it for you.

---

### Post by jaqian on 2009-09-23
Thanks. Will this also copy the folder structure?

---

### Post by rampageoberon on 2009-09-23
Rsync is an excellent package to use. I personally prefer mirrordir, which basically keeps an up-to-date duplicate copy of the given directory. It is usually over 2 different hard drives.

You can create a script and run as a cron job. A sample command is

```
 mirrordir -lv --no-netrc --no-chown --no-chmod /home/user/Documents /path-to-backup/Backup/
```

This backs up /home/user/Documents to another storage medium

---

### Post by badger_fruit on 2009-09-23
Yes, rsync is the way to do what you want
1. Create a human-readable log file? Yes.
2. Can be set to run at specific times? Yes. CRON job it.
3. Backup sub-folders and contents? Yes.

Example script I wrote
```

#!/bin/sh
LOG_FILE=/path/to?log/file/$(date '+%Y-%m-%d')-backup.log
echo >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
date >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
echo "Backup ==> bgrsvr-x" >> $LOG_FILE
rsync -avz /source/folder/  /target/folder/ >> $LOG_FILE 2>&1
echo "------------------------------" >> $LOG_FILE
echo "End" >> $LOG_FILE
echo "------------------------------" >> $LOG_FILE
echo "   " >> $LOG_FILE

```

Each rsync is logged to the $LOG_FILE and the log file name changes each day automatically to help me organise/cull as necessary

I love this webpage --> [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/) which gives intense detail on rsync (it's the man page but in nicer html format!)

This is called every 30 minutes from a cronjob

```
30 * * * *  /path/to/script/backup-script
```

---

