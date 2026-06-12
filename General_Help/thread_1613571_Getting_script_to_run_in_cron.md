---
title: "Getting script to run in cron"
date: 2010-11-04
forum: General Help
---

### Post by Trevor Burton on 2010-11-04
Hi everybody,

Hoping you can help me with this one.

Basic problem:
I have a working bash script to do backup - it runs fine from the terminal.  During the backup it makes a log file in my home area.
I transferred it to root, and set it up to run as a cron job as root.
It runs fine as long as I am logged in with my normal user name.
It does not run if I am not logged in.
Logs show the script was called by cron, but there is no output and no backing up is done.

Here is the script
```
#!/bin/bash

for i in `cat /proc/mounts | cut -d' ' -f2`; do
   if [ "$i" = "/media/Elrond" ]; then
			sudo rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
      exit
   fi
done
echo "Couldn't find Elrond, so am attempting to manually mount it"
sudo mkdir /media/Elrond
sudo mount -t ntfs-3g /dev/sdb1 /media/Elrond

			sudo rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
```

This script is saved as /root/dailybackup (I heard about avoiding . and file extensions).  root is the owner and file permissions are 755

Here is the crontab from 'sudo crontab -l'
```
SHELL=/bin/bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/root
# m h  dom mon dow   command
45 20 * * * /root/dailybackup
```

I heard about setting environment variables, but I'm not sure if I put them in the right place (the crontab).

Any ideas?

---

### Post by CharlesA on 2010-11-04
Take out sudo and use the full path to each command.

Also, you don't need to use a loop to check to see if that device is mounted.

Try using mountpoint, or grepping the output of "mount" instead.

---

### Post by DaithiF on 2010-11-04
> **Trevor Burton said:**
> 
It runs fine as long as I am logged in with my normal user name.
It does not run if I am not logged in.

Any ideas?

Is your home directory encrypted?

---

### Post by Trevor Burton on 2010-11-04
> **CharlesA said:**
> Take out sudo and use the full path to each command.

Also, you don't need to use a loop to check to see if that device is mounted.

Try using mountpoint, or grepping the output of "mount" instead.

Thanks CharlesA, will do the sudo thing (forgot to remove from the initial test script on my home area) - the loop is a bit stupid, but I was copying from something I found online. I'll try fixing it up later.

> **DaithiF said:**
> Is your home directory encrypted?

Hi DaithiF

Yes it is. Do you think it is failing because it can't create the log file as root in an encrypted home directory?

I'll report back on whether removing sudo works.

Trevor

---

### Post by Trevor Burton on 2010-11-04
OK, I think I got rid of sudo and put in the paths correctly, here is the script after my edits
```
#!/bin/bash

for i in `/bin/cat /proc/mounts | cut -d' ' -f2`; do
	if [ "$i" = "/media/Elrond" ]; then
		/usr/bin/rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
		exit
	fi
done

echo "Couldn't find Elrond, so am attempting to manually mount it"
/bin/mkdir /media/Elrond
/bin/mount -t ntfs-3g /dev/sdb1 /media/Elrond
/usr/bin/rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/

```


I checked the syslog and it showed
```
Nov  4 21:30:00 Thingol CRON[2260]: (root) CMD (/root/dailybackup)
```

So if I have this right, the script was executed under the root user.
"Elrond" did get mounted but no backups were done, and no log files were written to /home/trevor/backup_logs/

Is it the encryption, and could I send backup logs elsewhere?

Trevor

---

### Post by DaithiF on 2010-11-04
Yes the encryption will be a problem here.  rsync will neither be able to read (the excludes-file), nor write (to the log file).  You could change the location of these files to somewhere unencrypted (ie. outside your home directory).

i've no experience of encrypting a home dir, so I'm going to assume that the rsync itself will handle the encrypted home ok, ie. it will blindly copy the data irrespective of the fact that it is garbage as far as it knows.  I guess you'll end up with a byte-for-byte backup that you would have to unencrypt before you could do anything useful with it.

---

### Post by trikster_x on 2010-11-04
In your crontab, instead of putting just the path to the script, try having cron output to a log as well.  Paste the following in:
```
45 20 * * * /root/dailybackup >> /path/to/log 2>&1
```
This will send the stdout as well as stderr to the log file when the script attempts to run.  Then you will be able to see any errors that may not have been part of the stdout for the script.  If you post that, it may be easier for someone to pinpoint the problem.

---

### Post by Trevor Burton on 2010-11-04
> **DaithiF said:**
> Yes the encryption will be a problem here.  rsync will neither be able to read (the excludes-file), nor write (to the log file).  You could change the location of these files to somewhere unencrypted (ie. outside your home directory).

i've no experience of encrypting a home dir, so I'm going to assume that the rsync itself will handle the encrypted home ok, ie. it will blindly copy the data irrespective of the fact that it is garbage as far as it knows.  I guess you'll end up with a byte-for-byte backup that you would have to unencrypt before you could do anything useful with it.

OK, I'm trying to remember why I did the cron job as the root user.  I think it was to avoid using sudo and the password issues that would cause if I ran it as "trevor".  However, if I don't run it as "trevor" I hit the encryption issues. Am I stuck?

> **trikster_x said:**
> In your crontab, instead of putting just the path to the script, try having cron output to a log as well.  Paste the following in:
```
45 20 * * * /root/dailybackup >> /path/to/log 2>&1
```
This will send the stdout as well as stderr to the log file when the script attempts to run.  Then you will be able to see any errors that may not have been part of the stdout for the script.  If you post that, it may be easier for someone to pinpoint the problem.

Thanks trikster, I'll try that too to see if it confirms DaithiF's diagnosis.

I'll report back tomorrow.

Thanks you guys - that was such a fast response!

---

### Post by CharlesA on 2010-11-04
I'm not really sure how to do it with an encrypted home directory, unfortunately.

I have a similar script for my daily backups:

```
#!/bin/bash

###
### backup.sh
### Script to backup RAID Array
### Created by Charles
### Tested 10/04/2010
### Updated 10/04/2010
###

#Normal Variables
BIN=/bin/
USR=/usr/bin/
EMAIL=email@host
ARRAYPATH=/array/
DOCPATH=/docback/
HOME=/home/charles/
ERROR=${HOME}logs/daily_backup_error.log
DATE=$(${BIN}date +%D)
FOLDER=$(${BIN}date +%m%d%Y)

# Check if RAID Array is mounted, and if so, mount both backup drives by UUID.
if ${BIN}mountpoint -q $ARRAYPATH
then
  { ${BIN}mount -t ext4 UUID=49a8cdd0-a4fd-43e5-9c6e-3a4a3363b770 $DOCPATH; } 2> $ERROR || { echo "Mounting of backup drives failed" | ${USR}mail -s "Backup failed for $DATE" $EMAIL; exit; }
else
  { ${USR}mail -s "RAID Array not mounted! Backup Failed for $DATE" $EMAIL; exit; }
fi

# Variables for Doc Backup
OLDDOCNAME=$(${BIN}cat ${DOCPATH}latest)
NEWDOCDIR=$DOCPATH$FOLDER
OLDDOCDIR=$DOCPATH$OLDDOCNAME
DOCLOG=${DOCPATH}log/${FOLDER}.txt

# Check if Doc is mounted and if so, do a incremental backup of it.
if ${BIN}mountpoint -q $DOCPATH
then
  { ${BIN}cp --archive --link $OLDDOCDIR $NEWDOCDIR && echo $FOLDER > ${DOCPATH}latest && ${USR}rsync --archive --itemize-changes --delete --log-file $DOCLOG $ARRAYPATH --exclude dvds --exclude lost+found $NEWDOCDIR && ${BIN}umount $DOCPATH; } 2> $ERROR || { ${BIN}cat $ERROR | ${USR}mail -s "Doc Backup failed for $DATE" $EMAIL; }
fi
```

---

### Post by Trevor Burton on 2010-11-04
Thanks CharlesA, that is a useful thing to share - it will take me some time to study it though.

Here is the log from redirecting STDOUT and STDERR in cron

```
Couldn't find Elrond, so am attempting to manually mount it
/bin/mkdir: cannot create directory `/media/Elrond': File exists
rsync: failed to open exclude file /home/trevor/backup_logs/scripts/rsync-exclude: No such file or directory (2)
rsync error: error in file IO (code 11) at exclude.c(1062) [client=3.0.6]
```

I believe this confirms DaithiF's diagnosis that it is the encryption which is causing the problem.

This is difficult for me, as I need the encryption as I am dealing with personal data under the Data Protection Act, yet I also need backup to ensure data security.  One will have to give way.

I'm not sure what to do now, as encryption is vital in case of burglary.

Perhaps I arrange a script to run to a drive which doesn't need mounting, say a network share for backup?

Anyway, may I just thank you all for your help, I am amazed at how much community support there is.  I can't pay you back, but perhaps in the future I might be able to help others in a similar way.  Thanks so much.

---

### Post by trikster_x on 2010-11-05
Just something I thought I would point out about your script and the stdout/stderr from the cron log:

It seems to me that your script, as it is written in this post, will execute the same rsync command twice if the directory /media/Elrond exists.  I only say this because the second half of your script is outside of your conditional "if" statement that looks for the existence of /media/Elrond.  Also, in the cron log, it says /media/Elrond already exists.  You may want to work the echo, mkdir, mount, and rsync commands into your conditionals, or when you do get the script working it will be doing twice as much work as necessary, which means twice as much room for an error to occur.  Something along the lines of:
```
#!/bin/bash

if [ -a /media/Elrond ]
   then sudo rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
   else echo "Couldn't find Elrond, so am attempting to manually mount it" && sudo mkdir /media/Elrond && sudo mount -t ntfs-3g /dev/sdb1 /media/Elrond && sudo rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
fi
```
might work a bit better.  Not too sure whether or not the "-a" option applies to checking the existence of directories, but you can adjust that part as necessary.

As for dealing with the encrypted directory, have you attempted to run the script minus the "--exclude-from" and "--log-file" options?  The cron log may suffice for catching any info generated by the verbose output, and the only way for "rsync" to actually read the exclude file is to have it decrypted before use.  This of course is pointless unless you decrypt the entire directory so "rsync" can read the file info to apply the exclusions.  It may be that you simply cannot use "--exclude-from" in this instance.  Just my last two cents on the subject :D

---

### Post by DaithiF on 2010-11-05
> **Trevor Burton said:**
> This is difficult for me, as I need the encryption as I am dealing with personal data under the Data Protection Act, yet I also need backup to ensure data security.  One will have to give way.

I'm not sure what to do now, as encryption is vital in case of burglary.



Just move the exclude-file (and log file destination) somewhere that isn't encrypted ... only your home dir is encrypted, so for example somewhere under /etc for the exclude file, and perhaps /var/log/ for the logfile.

---

### Post by dcstar on 2010-11-05
> **DaithiF said:**
> Just move the exclude-file (and log file destination) somewhere that isn't encrypted ... only your home dir is encrypted, **so for example somewhere under /etc for the exclude file**, and perhaps /var/log/ for the logfile.

No, **do not put user files in system folders**. System folders are for the system. /etc is a system folder.

Create a new folder outside of the default system folders (use whatever name makes sense to you):

```
sudo mkdir /mytools
```
10 seconds of typing can prevent future, unnecessary complications.

---

### Post by trikster_x on 2010-11-05
> **DaithiF said:**
> Just move the exclude-file (and log file destination) somewhere that isn't encrypted ... only your home dir is encrypted, so for example somewhere under /etc for the exclude file, and perhaps /var/log/ for the logfile.

Sorry if this is completely incorrect, but how does moving the exclude file address the problem of trying to read an encrypted directory?  If "rsync" can't find the file with the exclude list while it is encrypted, then it won't see any of the files it is supposed to exclude.

If you really want to avoid extraneous files in your encrypted backup, you might try setting up a single encrypted directory within your /home, and move all your sensitive data their, then removing encryption from the rest of your /home folder.  [Truecrypt]("http://linuxandfriends.com/2010/02/03/how-to-truecrypt-setup-on-ubuntu-linux/") would do this efficiently.  Using [seahorse]("http://www.webupd8.org/2009/10/encrypt-files-and-folders-in-ubuntu.html") you could simply remove the encryption from /home and encrypt existing files individually.  It might be a bit more work accessing individual files through a program, so I don't know which would fit your situation better.

---

### Post by DaithiF on 2010-11-05
> **trikster_x said:**
> Sorry if this is completely incorrect, but how does moving the exclude file address the problem of trying to read an encrypted directory?  If "rsync" can't find the file with the exclude list while it is encrypted, then it won't see any of the files it is supposed to exclude.

Yes I think you're absolutely right.  I wasn't sure if the filenames themselves were encrypted -- but it turns out they are.

---

### Post by Trevor Burton on 2010-11-06
I've had a thought.

If this cron job ran from the user "trevor" (who owns the encrypted home folder )instead of "root" will it work OK?

If so, my only problem is ensuring the external hard drive is mounted.  I could do this from a script that ran as root a couple of minutes before each backup job.

What do you think?

---

### Post by CharlesA on 2010-11-06
I don't know much about the whole encrypted home dir thing outside of it being decrypted silently once you login.

Can't hurt to try right?

---

### Post by Trevor Burton on 2010-11-06
Right.

I've also discovered how to mount the external drive at startup using fstab, so I don't even need to mount it in cron.  Whether the permissions will be OK if it is mounted at startup I don't know, but it does let "trevor" create new files, so I'll have a go at running the backup script from "trevor"'s cron and see what happens.

Trevor

---

### Post by btindie on 2010-11-06
The script could be simplified and rewritten in the following way:
```
#/bin/sh

if [ "$(id -u)" != "0" ]; then
    sudo "$0"
    exit $?
fi

[ -d /media/Elrond ] || mkdir /media/Elrond

if ! mountpoint -q /media/Elrond; then
    mount -t ntfs-3g /dev/sdb1 /media/Elrond
fi

rsync -av --progress --delete --log-file=/home/trevor/backup_logs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backup_logs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/

```It makes sure all conditions are met before running rsync.

Schedule the script to run via cron with user trevor. When it runs it will re-execute itself as root. To be able to do that without having to enter a password you'll have to edit /etc/sudoers with **visudo** adding the following lines to allow user trevor to run the backup script as root.

```
Cmnd_Alias    BACKUP = /path/to/dailybackup

trevor    ALL = NOPASSWD: BACKUP
```That may then get around your encrypted homedir and rights problem.

Edit: Just seen your post about using fstab to mount the partition - there's no harm in checking if it's mounted or not and mounting it if required.

---

### Post by Trevor Burton on 2010-11-06
> **btindie said:**
> The script could be simplified and rewritten in the following way: ...

Thanks btindie.

I've just tried mounting the backup drive in fstab, and it seems to work ok.  Then I've put the backup script in trevor's crontab, but it doesn't work.

the syslog shows
```
Nov  6 17:53:01 Thingol CRON[4977]: (trevor) CMD (/home/trevor/backuplogs/scripts/dailybackup >> 2>&1 /mylogs/diagnostic)

```

but nothing appears in /mylogs/diagnostic at all, which is a bit confusing.

The actual backup script that is in dailybackup was

```
sudo rsync -av --progress --delete --log-file=/home/trevor/backuplogs/$(date +%Y%m%d%H%M%S)_daily_rsync.log --exclude-from="/home/trevor/backuplogs/scripts/rsync-exclude" /home /media/Elrond/Backups/Thingol-Ubuntu/daily_home/
```

Not sure why I didn't get any errors recorded in /mylogs/diagnostic - did I mistype something?

I think my next step is to try btindie's suggestion above.

---

### Post by trikster_x on 2010-11-06
Move "2>&1" to the end of the crontab entry

---

### Post by btindie on 2010-11-06
The command to run your script from cron should be
```
/home/trevor/backuplogs/scripts/dailybackup >>/mylogs/diagnostic  2>&1
```

---

### Post by Trevor Burton on 2010-11-06
I'm an idiot.

The script didn't have execute permissions, and it called sudo.

Have now fixed these and I'm experimenting - will report back.

---

### Post by Trevor Burton on 2010-11-06
> **btindie said:**
> The script could be simplified and rewritten in the following way: ....

...
Schedule the script to run via cron with user trevor. When it runs it will re-execute itself as root. To be able to do that without having to enter a password you'll have to edit /etc/sudoers with **visudo** adding the following lines to allow user trevor to run the backup script as root.


Just tested this, and (fingers crossed!) I think it is all working.

Fantastic!

Could I just trouble you with a couple of queries, because while I am familiar in general with programming, I am a bash newbie...

what is the syntax in 
```
if [ "$(id -u)" != "0" ]; then
    sudo "$0"
    exit $?
fi
```
I understand that this is meant to re-execute as root, but I don't understand how it works.

What does the following?  I don't get what the bracket symbols do but it seems to be some sort of existence check for the directory?
```
[ -d /media/Elrond ]
```

and I'm guessing the following is a kind of "then" statement to make the directory if it doesn't exist?
```
|| mkdir /media/Elrond
```

Many thanks for your help btindie, I honestly didn't think I'd find a way out of this :P

Trevor

---

### Post by CharlesA on 2010-11-06
> **Trevor Burton said:**
> Just tested this, and (fingers crossed!) I think it is all working.

Fantastic!

Could I just trouble you with a couple of queries, because while I am familiar in general with programming, I am a bash newbie...

what is the syntax in 
```
if [ "$(id -u)" != "0" ]; then
    sudo "$0"
    exit $?
fi
```
I understand that this is meant to re-execute as root, but I don't understand how it works.

That checks to see if root is running the script, and if not, runs it with sudo.

> What does the following?  I don't get what the bracket symbols do but it seems to be some sort of existence check for the directory?
```
[ -d /media/Elrond ]
```

and I'm guessing the following is a kind of "then" statement to make the directory if it doesn't exist?
```
|| mkdir /media/Elrond
```

Many thanks for your help btindie, I honestly didn't think I'd find a way out of this :P

Trevor

As for that one, the -d part checks to see if a directory exists or not.

It would look something like this:

```
if [[ -d /path/to/some/dir ]]
then
do this
else
do that
fi

```

---

### Post by trikster_x on 2010-11-06
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html")
Here is a pretty in depth guide to BASH.  The page linked is an explanation of the basic usage of "if", along with some of the primary expressions like the [ -d /file/path ] in your script.  Very good info to keep bookmarked while learning the ways of BASH

---

### Post by Trevor Burton on 2010-11-06
Thanks to all of you for your help (and the bash tutorial link).

Not only do I have a working backup, but I actually understand how it works.

Many many thanks.

I'll switch the thread to SOLVED

---

