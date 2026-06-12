---
title: "Cron job executing bash file fails"
date: 2012-04-20
forum: General Help
---

### Post by sbarrow on 2012-04-20
I have a bash file I've created for backup purposes. This is a very basic bash file. If I execute the bash file from a terminal it is fine, backup tar file is created, when it finishes it is near 3GB. When I have a cron job execute it, I see the tar file but stops growing at 15.8MB. Can't seem to figure out where it will log the any errors and how to look at them. Any help is very much appreciated.

---

### Post by hakermania on 2012-04-20
Hello!
This means that the file executes but it fails while doing the job? Have you confirmed this (has this happen more than once)?
Have you tried Deja-dup ? It's nice and installed by default.

---

### Post by sbarrow on 2012-04-20
> **hakermania said:**
> Hello!
This means that the file executes but it fails while doing the job? Have you confirmed this (has this happen more than once)?
Have you tried Deja-dup ? It's nice and installed by default.

Yes it happens whenever the job is executed by cron. If I manually execute the bash file it completes. Happens everytime. No idea what Deja-dup is.

---

### Post by drdos2006 on 2012-04-20
Add a log file in your script, then look at the log file.

--log-file=/home/ne-user/Documents/backup-log-home.txt

sort of thing.

regards

---

### Post by papibe on 2012-04-20
Would it be possible for you to post your script, so we can take a look?

Regards.

---

### Post by sbarrow on 2012-04-20
So here is what is strange. My tar command is the last command in my bash script. If I add the logfile piece to the command as shown below 

 * original: 
tar cvpzf $BUFn $BUDir --exclude=$BUDir/lost+found

 * Changed to: 
LOGFILE=$BULoc'/backup-log.txt'
tar cvpzf $BUFn $BUDir --exclude=$BUDir/lost+found > $LOGFILE


It seems to execute correctly. I've tested removing the logfile piece of it, making sure there was no trailing spaces or line feeds, and even adding a sleep 10 to the end of the bash script and nothing works unless I have the logfile piece of it in there. No big deal, good to have it anyway, but strange none the less.

---

### Post by JKyleOKC on 2012-04-20
I suspect that the critical difference is not presence or absence of the log file itself, but rather the fact that redirecting output of tar to it guarantees that "stdout" is defined. When cron runs a job, it does so as "root" rather than as your user, and it's possible that stdout could be either undefined, or directed to a file in an area with limited or no available space for writing.

Most of the system-supplied cron jobs seem to direct output, both stdout and stderr, to /dev/null and this might be a solution to your situation. However this would discard any output, so directing to a log file might be the preferable solution...

---

### Post by CharlesA on 2012-04-20
Having output echo to stdout shouldn't cause it to fail.

Try using full paths.

---

### Post by JKyleOKC on 2012-04-20
Agree that it ought not have any effect, but that seems to be the only significant difference between "working" and "not working" versions of the script. If it were a question of full versus relative paths, I would expect both versions to fail...

---

### Post by CharlesA on 2012-04-20
> **JKyleOKC said:**
> Agree that it ought not have any effect, but that seems to be the only significant difference between "working" and "not working" versions of the script. If it were a question of full versus relative paths, I would expect both versions to fail...
The user and cron have different environments, so it's always a good idea to use full paths when writing something to run in cron.

---

### Post by JKyleOKC on 2012-04-20
Again, I agree fully. However the OP never posted the full script, and the paths are all defined in variables that are expanded in the snippets posted, so we can't see whether they are absolute or not. My belief is that if they were not already absolute then the cron job would not execute when the LOGFILE was added...

In other words, while the point is totally valid, it doesn't seem to apply in this specific situation.

---

### Post by sbarrow on 2012-04-20
So even with full paths it failed at the same point. I originally was running the cron job as my username, so thought I would change it to root for testing and that too didn't seem to make a difference.

---

### Post by sbarrow on 2012-04-20
Here is my complete script. 
[INDENT]
#! /bin/bash
clear

#Location to put backup
BULoc="/media/SBED1TB/Backups"

#Location to backup
BUDir="/media/HD2/SambaShares"

RunD=$(date +%d)

if [ "$RunD" = 1 ]
then 
#FileName to backup
RunD=$(date +%Y-%B)
BUFn="$RunD-Backup.tgz"
else
BUFn="$RunD-Backup.tgz"
fi

cd $BULoc
# Remove tar file if it already exists
rm $BUFn

clear
LOGFILE=$BULoc'/'$BUFn'-log.txt'
tar cvpzf $BUFn $BUDir --exclude=$BUDir/lost+found

[/INDENT]

---

