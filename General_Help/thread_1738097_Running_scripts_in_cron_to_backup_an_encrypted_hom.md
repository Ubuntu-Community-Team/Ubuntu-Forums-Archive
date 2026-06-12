---
title: "Running scripts in cron to backup an encrypted home drive"
date: 2011-04-24
forum: General Help
---

### Post by Trevor Burton on 2011-04-24
Hi all, hoping you can help.

A little while ago I got some help to do the above (thanks CharlesA, DaithiF, trikster_x, dcstar, btindie), and it was all working.  Unfortunately, I had a major system crash and while the backups helped restore my files, I had stupidly excluded the backup scripts from the backing up!

The thread helping me was 
[http://ubuntuforums.org/showthread.php?t=1613571](http://ubuntuforums.org/showthread.php?t=1613571)

I've now re-written everything and here's the problem.

There are two backup scripts, hourlybackup and dailybackup

They both run fine when I am logged in [COLOR="Red"]but not when there is nobody logged on to the machine[/COLOR].

My home drive is encrypted, so I have to run the script as my username (trevor) to decrypt the home drive.
However, I need to be root to mount the backup hard disk, so the script immediately re-executes itself using sudo.  
This way I can decrypt (as trevor) and be sudo to mount.
This was all suggested in 
[http://ubuntuforums.org/showthread.php?t=1613571](http://ubuntuforums.org/showthread.php?t=1613571)
It definitely worked before my big crash, although obviously something is now wrong as it isn't working now.

Here's my crontab ...
```
SHELL=/bin/bash
path=/bin:/sbin:/usr/bin:/usr/sbin:/root

# m h  dom mon dow   command
15 23 * * * /home/trevor/scripts/dailybackup > /home/trevor/backup_logs/tmp_log 2>&1
01 7-23 * * * /home/trevor/scripts/hourlybackup > /home/trevor/backup_logs/tmp_log 2>&1
```

Here's my sudoers file ...
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias	BACKUP	= 	/home/trevor/scripts/hourlybackup, \
				/home/trevor/scripts/dailybackup, \
				/home/trevor/scripts/test

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# trevor is allowed to run backup scripts without a password
trevor	ALL	= NOPASSWD: BACKUP
```

Here's my hourly backup script (it keeps entirely separate backups at 1 min past each hour from 7-23 - I know it's clunky especially re: the logfile and I welcome improvements to the script but it is the fact it isn't running that is a problem)....
(PS Elrond is my name for the backup drive which isn't always mounted, so there is a bit of code to check for this and mount it if not)
```
#!/bin/bash

# Backup script for the home partition of Thingol
# Written by Trevor Burton - April 22nd 2011
# Last modified by Trevor Burton - April 22nd 2011
# 
# Lots of help from the Ubuntu community
# http://ubuntuforums.org/showthread.php?p=10072677#post10072677
#
# this script is executed once per hour via the user trevor's crontab
# the user trevor needs to be in the sudoers file with 
# Cmd_Alias BACKUP = /home/trevor/scripts/hourlybackup (or whatever this script is called)
# trevor ALL = NOPASSWD: BACKUP
#

##############################################################################
#
# First re-execute with sudo
# This ensures the encrypted home directory for trevor is decrypted for backup
# but still allows privileged use
# entries in the sudoers file allows this (see top)
#
##############################################################################

if [ "$(id -u)" != "0" ]; then
  sudo "$0"
  exit $?
fi

##############################################################################
#
# Normal Variables
#
##############################################################################

BIN=/bin/

TREVOR=/home/trevor
LOGS=${TREVOR}/backup_logs/

DATE=$(${BIN}date +%Y_%m_%d)
DATETIME=$(${BIN}date +%Y_%m_%d_%H%M%S)
HOUR=$(${BIN}date +%H)
LOGFILE=${LOGS}hourly_${HOUR}_rsync.log

EXCLUDE=${LOGS}/rsync-exclude
SOURCE=/home/
ELROND=/media/Elrond/
BACKUP=${ELROND}Backups/Thingol-Ubuntu/
TARGET=${BACKUP}hourly_${HOUR}/

##############################################################################
#
# Write headers to the log file
#
##############################################################################

echo "###" > $LOGFILE
echo "### HOURLY backup" >> $LOGFILE
echo "###" >> $LOGFILE;
echo "### Beginning rsync backup of $SOURCE" >> $LOGFILE;
echo "### to $TARGET" >> $LOGFILE;
echo "### on $(${BIN}date)" >> $LOGFILE;
echo "###" >> $LOGFILE;


##############################################################################
#
# Next check that Elrond is mounted 
#
##############################################################################

if ! mountpoint -q $ELROND; then
	echo "### Mounting Elrond at $DATETIME" >> $LOGFILE
	[ -d /media/Elrond/ ] || sudo mkdir $ELROND
	mount -t ntfs-3g /dev/sdb1 $ELROND 2>> $LOGFILE || { echo "Mounting of backup drives failed" >> $LOGFILE; exit; }
	echo "###" >> $LOGFILE
fi

echo "### About to backup up to $TARGET" >> $LOGFILE
echo "###" >> $LOGFILE

##############################################################################
#
# Execute the hourly backup
#
##############################################################################

rsync -av --progress --delete --log-file=$LOGFILE --exclude-from=$EXCLUDE $SOURCE $TARGET
```

I've checked the system logs, and the scripts are started by CRON, but nothing is backed up and no output appears (unless I am logged in in which case they work fine).

I'e done a lot of googling and came across the visiblepw option for sudo, tried it but it didn't help.

I'm now stuck.

Any ideas?

Many thanks in advance

---

### Post by Trevor Burton on 2011-04-24
<bump>
anyone?

---

### Post by CharlesA on 2011-04-25
As far as I know, you need to be logged in for your home directory to be decrypted.

That's probably what is causing the script not to run (or it runs and fails)

---

### Post by Trevor Burton on 2011-04-25
> **CharlesA said:**
> As far as I know, you need to be logged in for your home directory to be decrypted.

That's probably what is causing the script not to run (or it runs and fails)

Thanks for the reply CharlesA.

Maybe my memory is tricking me, but I thought I had it working before my crash.  That was what re-executing as sudo was for. Somehow it allowed decryption, but also gave root rights to mount the backup drive.

Mind you, my memory is not perfect!

---

### Post by Trevor Burton on 2011-04-25
I've been thinking about what you said CharlesA. If I put the backup drive in /etc/fstab so it is mounted at startup, and comment out the bit about re-starting in sudo, it should work.

I'll give that a go and report back.

Trevor 

PS It would break if the backup drive had been unmounted, but if I put the mountpoint and mount commands in visudo for user "trevor", even that bit would work. I'll just try the top bit first.

---

### Post by trikster_x on 2011-04-25
Okay, so off the top of my head here, are you running the cron job using you user's crontab, or are you running using ROOT's crontab?  

Crontab events in a user's cron will only run while the user is logged in.  If you did not run:```
sudo crontab -e
```then this is probably where your problem lies.  ROOT crontab events run regardless of the user logged in.  Also keep in mind someone HAS to be logged in for any crontab jobs to run at all.  A side note is that a ROOT crontab job should not need a password for sudo commands since it is being run as ROOT anyway. As always, take extra care when automating any job with ROOT priviliges.

---

### Post by CharlesA on 2011-04-25
> **trikster_x said:**
> 
Crontab events in a user's cron will only run while the user is logged in.

That hasn't been my experience. I've got a few commands that run in my user's crontab on my server and I'm rarely logged on.

It might be different if the home directory is encrypted tho.

---

### Post by trikster_x on 2011-04-25
> **Trevor Burton said:**
> I've been thinking about what you said CharlesA. If I put the backup drive in /etc/fstab so it is mounted at startup, and comment out the bit about re-starting in sudo, it should work.

Yes, you can do this, but you have to remember that it will be auto-mounted for all users. So from a security standpoint, not such a great idea.  You are better off mounting, backing-up, and un-mounting through the script.  Then it minimizes the possibility of someone practicing their decryption techniques on your drive.

> **CharlesA said:**
> That hasn't been my experience. I've got a few commands that run in my user's crontab on my server and I'm rarely logged on.

It might be different if the home directory is encrypted tho.

[Ubuntu-Cron HowTo]("https://help.ubuntu.com/community/CronHowto")

> Each user has a crontab file which specifies the actions (and times at which they should be executed) only executed when that user is logged in.

You probably have cron or your user priviliges set up differently than the average Ubuntu user.

EDIT:
So I reread the initial post and it seems that the problem is you can't run the script without someone being logged in.  Unfortunately, there is no way to run a cron job unless the user who owns the cron job is logged in or it is run as ROOT with any user logged in.  Either way [color=red]SOMEONE HAS TO BE LOGGED IN.[/color]  There are no ifs ands or buts about that fact.  Cron does not load until a user account becomes active.

Looking back at your original thread, your script could only be run as written while logged into "trevor" because you needed to access an encrypted file for your excludes.  Only way to do that is to be logged in.  Are you absolutely certain the script ran the way you think it did before your crash?  

As it is written RIGHT NOW, you have to be logged into "trevor" because you still are using an exclude file.  Since /home/trevor is encrypted until log in, there is no way for the script to read the exclude file unless you decrypt the /home directory.  If you move the exclude file out of /home/trevor, rsync still won't be able to read the directories and filenames in the encrypted folder.

Basically, your original script would never have run while not logged in and neither will this one.  I am at work now, but I can look to see if there is a way to decrypt your home directory from another user when I get home and help you work up another script to do so.  But someone will ALWAYS have to be logged on to be able to run the script through cron.

---

### Post by CharlesA on 2011-04-25
> **trikster_x said:**
> 
[Ubuntu-Cron HowTo]("https://help.ubuntu.com/community/CronHowto")

You probably have cron or your user priviliges set up differently than the average Ubuntu user.

Interesting, I'm just running a default install of Ubuntu Server 10.04. Same thing happens on a default install of Ubuntu Desktop.

*shrug*

---

### Post by trikster_x on 2011-04-25
> **CharlesA said:**
> Interesting, I'm just running a default install of Ubuntu Server 10.04. Same thing happens on a default install of Ubuntu Desktop.

*shrug*

That's odd, because I have a couple user accounts on my home desktop.  Each has a different set of cron jobs, as each account serves a different purpose.  Neither runs the other's cron jobs.  If I want to run a job cross account, I have to either put it in each account or run as a ROOT job.

---

### Post by CharlesA on 2011-04-25
> **trikster_x said:**
> That's odd, because I have a couple user accounts on my home desktop.  Each has a different set of cron jobs, as each account serves a different purpose.  Neither runs the other's cron jobs.  If I want to run a job cross account, I have to either put it in each account or run as a ROOT job.
Interesting.

Running 10.10? Wonder if there was a change between 10.04 and 10.10. Altho, I've had the same thing occur since I started using 9.04.

---

### Post by Trevor Burton on 2011-04-25
> **trikster_x said:**
> Okay, so off the top of my head here, are you running the cron job using you user's crontab, or are you running using ROOT's crontab?  

Crontab events in a user's cron will only run while the user is logged in.  If you did not run:```
sudo crontab -e
```then this is probably where your problem lies.  ROOT crontab events run regardless of the user logged in.  Also keep in mind someone HAS to be logged in for any crontab jobs to run at all.  A side note is that a ROOT crontab job should not need a password for sudo commands since it is being run as ROOT anyway. As always, take extra care when automating any job with ROOT priviliges.

Wow, I'm really surprised by that!
I've set up the cron job as a standard user, not root.
It has to be a standard user as it is the user's home drive that is encrypted and I want to decrypt it to back it up (actually that sounds silly).

I did not realise that someone has to be logged in for any cron job to run - doesn't that mean backups won't take place unless someone is logged in - seems to kill backup strategies which are based on cron.

Can I run a cron job from root's crontab, but run it as a user to get the decryption?

Or maybe I should increase my physical security so I could dispense with the encryption which seems to be the cause of my woes.

---

### Post by Trevor Burton on 2011-04-25
> **trikster_x said:**
> 
Looking back at your original thread, your script could only be run as written while logged into "trevor" because you needed to access an encrypted file for your excludes.  Only way to do that is to be logged in.  Are you absolutely certain the script ran the way you think it did before your crash? 

Well, no I am not absolutely certain.  In fact you've convinced me I'm wrong! 

> **trikster_x said:**
> As it is written RIGHT NOW, you have to be logged into "trevor" because you still are using an exclude file.  Since /home/trevor is encrypted until log in, there is no way for the script to read the exclude file unless you decrypt the /home directory.  If you move the exclude file out of /home/trevor, rsync still won't be able to read the directories and filenames in the encrypted folder.

Basically, your original script would never have run while not logged in and neither will this one.  I am at work now, but I can look to see if there is a way to decrypt your home directory from another user when I get home and help you work up another script to do so.  But someone will ALWAYS have to be logged on to be able to run the script through cron.

Trikster_x, thanks for your reply here.  I'm struggling a little to see how I can really use cron for a backup strategy.  Unless I happen to be logged in when cron fires up the script, I won't get any backups, even if the script are executed as root (let's ignore the encryption/decryption problem for now).  Is that right?  How do servers backup their files if no-one is logged in?  Is it not done from cron?

---

### Post by Trevor Burton on 2011-04-25
> **CharlesA said:**
> Interesting.

Running 10.10? Wonder if there was a change between 10.04 and 10.10. Altho, I've had the same thing occur since I started using 9.04.

I'm running 10.04

---

### Post by trikster_x on 2011-04-25
Okay, just tested cron's capabilities on my 10.10 laptop:

Cron will run cross account.  No need to be logged into the user accountwith the crontab.

Cron will run with no account logged in.  No need to log in whatsoever.

Verified both of these by creating a cron job that created a log file on my desktop.  Created the file under both circumstances.  Looks like the help page is due for a rewrite.  My apologies to you charles a, you were exactly right.

With that out of the way, even with your cron trying to run while not logged into the account that owns the home directory, you may still need to log in to decrypt it. Though I am not completely sure about this either.  I will do more testing when I get home and see what I can come up with.

EDIT:

I think I found something in your script that could be contributing to the problem.  When you specify $SOURCE, you are specifying every home directory available to the installation:
```
SOURCE=/home/
```
is what you have.
```
SOURCE=/home/trevor
```
Is what you may need.
Of course I'm not batting a high average today, so I may be wrong here too...

Also, I noticed you used sudo to create the directory elrond, but didn't use sudo to mount OR rsync.  You may need to throw the sudo before those two commands to get them to work right.

---

### Post by CharlesA on 2011-04-25
@trikster_x: Happens to everyone. :) I am glad you were able to confirm the behavior.

@OP: I've not really dealt with encryption since I read some horror stories about it and backups, ssh, etc.

It could be that the script won't run unless you are logged in since it decrypts your home directory then.

It looked like you have the cronjob set to send the output to a file, does that file say anything?

---

### Post by trikster_x on 2011-04-26
Okay, I tried running the script on an unencrypted /home directory on my comp when I got home, And the first thing I noticed was that when it was looking for the exclude file, it was looking for ```
/home/"user"/backup_logs//rsync-exclude
```  I am pretty sure you want it to look in:```
/home/"user"/backup_logs/rsync-exclude
```
Correct me if I'm wrong.

I fixed that bit of code below.  When you are setting up location variables it is a good idea to never end with a trailing "/", just to keep writing locations using the variable as natural as possible. 

```
#!/bin/bash

# Backup script for the home partition of Thingol
# Written by Trevor Burton - April 22nd 2011
# Last modified by Trevor Burton - April 22nd 2011
# 
# Lots of help from the Ubuntu community
# http://ubuntuforums.org/showthread.php?p=10072677#post10072677
#
# this script is executed once per hour via the user trevor's crontab
# the user trevor needs to be in the sudoers file with 
# Cmd_Alias BACKUP = /home/trevor/scripts/hourlybackup (or whatever this script is called)
# trevor ALL = NOPASSWD: BACKUP
#

##############################################################################
#
# First re-execute with sudo
# This ensures the encrypted home directory for trevor is decrypted for backup
# but still allows privileged use
# entries in the sudoers file allows this (see top)
#
##############################################################################

if [ "$(id -u)" != "0" ]; then
  sudo "$0"
  exit $?
fi

##############################################################################
#
# Normal Variables
#
##############################################################################

BIN=/bin

TREVOR=/home/trevor
LOGS=${TREVOR}/backup_logs

DATE=$(${BIN}/date +%Y_%m_%d)
DATETIME=$(${BIN}/date +%Y_%m_%d_%H%M%S)
HOUR=$(${BIN}/date +%H)
LOGFILE=${LOGS}/hourly_${HOUR}_rsync.log

EXCLUDE=${LOGS}/rsync-exclude
SOURCE=/home/trevor
ELROND=/media/Elrond/
BACKUP=${ELROND}Backups/Thingol-Ubuntu/
TARGET=${BACKUP}hourly_${HOUR}/

##############################################################################
#
# Write headers to the log file
#
##############################################################################

echo "###" > $LOGFILE
echo "### HOURLY backup" >> $LOGFILE
echo "###" >> $LOGFILE;
echo "### Beginning rsync backup of $SOURCE" >> $LOGFILE;
echo "### to $TARGET" >> $LOGFILE;
echo "### on $(${BIN}date)" >> $LOGFILE;
echo "###" >> $LOGFILE;


##############################################################################
#
# Next check that Elrond is mounted 
#
##############################################################################

if ! mountpoint -q $ELROND; then
	echo "### Mounting Elrond at $DATETIME" >> $LOGFILE
	[ -d /media/Elrond/ ] || sudo mkdir $ELROND
	mount -t ntfs-3g /dev/sdb1 $ELROND 2>> $LOGFILE || { echo "Mounting of backup drives failed" >> $LOGFILE; exit; }
	echo "###" >> $LOGFILE
fi

echo "### About to backup up to $TARGET" >> $LOGFILE
echo "###" >> $LOGFILE

##############################################################################
#
# Execute the hourly backup
#
##############################################################################

rsync -av --progress --delete --log-file=$LOGFILE --exclude-from=$EXCLUDE $SOURCE $TARGET
```

And this did start while I was logged out on my home comp.

EDIT:

Okay, the code above is what you need.  I tested it on my home system using an encrypted home directory while sitting at the log in screen.  Backed up my entire encrypted home folder.  I checked it specifying SOURCE as /home/ as well, and it did as I thought and started backing up every home folder.  I suppose you could exclude the other home directories, but specifying the home directory you want as the source is better.

For some reason, my exclude file didn't work how I would imagine it was supposed to, but that could be a failure on my part to use the correct syntax in my exclude list.  Other than that, as long as "rsync-exclude" is in /home/trevor/backup_logs then this should run fine for you.  

I didn't check the mounting portion because I don't like messing with my fstab enough to bother.  Besides, I didn't see anything wrong with the mount portion of the script.

---

### Post by CharlesA on 2011-04-26
Nice job, trikster_x.

So basically, you need to execute a script as the user in order to decrypt the home directory, then use sudo to run it as root to do the backup.

Is that correct?

I'm not quite sure I understand.

---

### Post by trikster_x on 2011-04-26
basically, yeah.  running the script as a user seems to do some kind of pseudo log in or something.  

Basically there were two things wrong with the script:

1. the script was looking one directory too low for the excludes file.  This caused an error as soon as it tried to run rsync

2. the script attempted to back up ALL home directories available.  I don't know if this was by design, but it makes more sense to me to specify just the directory you want to back up.

So fixing those two things made this script run likea champ, at least on my compuer.

Sorry for so many wrong leads yesterday, I was at work most of the time, so I couldn't do any real thorough trsting.  basically just on my breaks and when I could sneak a minute or two.

One thing to keep in mind, trevor, is that if you have error logs those are always the most helpful things you can post, since they say exactly what the problem is.  It makes troubleshooting mucheasier and can even lead you to the right solution without too many questions.

---

### Post by Dave_L on 2011-04-26
Does this decrypt your /home directory without the need to provide either the login password or the ecryptfs passphrase? If so, that's a big security hole in ecryptfs.

Or do I misunderstand what you're doing?

---

### Post by trikster_x on 2011-04-26
That is a good question.  I never considered trying to run the script from another user to see if you could get it to decrypt the directory, since being in /etc/sudoers basically exempts you from the password requirement for whatever scripts you are allowed to run.  You might look into that if you have the chance, Trevor.  I know I will be when i get home today.  Could be a major security issue for you, if other users have sudo power on your computer.

EDIT:

After some initial testing, it seems that the way the script is set up will not allow any other users to access any of the encrypted information.  ecryptfs mounts and unmounts the directory only after the user's login allows it to do so.  A user's cron must supply the necessary info so long as there are privileges set in sudoers to allow running the script as ROOT after it has started under the user's cron jobs.

---

### Post by Trevor Burton on 2011-04-29
> **CharlesA said:**
> @OP: I've not really dealt with encryption since I read some horror stories about it and backups, ssh, etc.

It could be that the script won't run unless you are logged in since it decrypts your home directory then.

It looked like you have the cronjob set to send the output to a file, does that file say anything?

Hi CharlesA,

Not had any problem with the encryption, except this backup issue.  I think you're right.  I have to be logged in to decrypt the home directory.  When I am not logged in cron can't access my backup script because it is encrypted (and so is the filename) and that is why I get no output from the output file :(

I think my only course now is to remove the encryption.

Trevor B

---

### Post by Trevor Burton on 2011-04-29
That's great - I thought I was completely out of luck.

I'll give that a go and post back here.

Trevor

PS, I did actually want to back up my other users' home directories too, but I'll start with your script as that should work, then branch out from there.

> **trikster_x said:**
> basically, yeah.  running the script as a user seems to do some kind of pseudo log in or something.  

Basically there were two things wrong with the script:

1. the script was looking one directory too low for the excludes file.  This caused an error as soon as it tried to run rsync

2. the script attempted to back up ALL home directories available.  I don't know if this was by design, but it makes more sense to me to specify just the directory you want to back up.

So fixing those two things made this script run likea champ, at least on my compuer.

Sorry for so many wrong leads yesterday, I was at work most of the time, so I couldn't do any real thorough trsting.  basically just on my breaks and when I could sneak a minute or two.

One thing to keep in mind, trevor, is that if you have error logs those are always the most helpful things you can post, since they say exactly what the problem is.  It makes troubleshooting mucheasier and can even lead you to the right solution without too many questions.

---

### Post by trikster_x on 2011-04-29
I see.  I wasn't sure if backing up the rest of your home directories was a goal for this script, that's why I changed the SOURCE variable.  If you need to back up the rest of the home directories, simply change SOURCE back to /home rather than /home/trevor and it will work the way you intend.  Let us know how it works for you.

---

### Post by Trevor Burton on 2011-05-07
> **trikster_x said:**
> I see.  I wasn't sure if backing up the rest of your home directories was a goal for this script, that's why I changed the SOURCE variable.  If you need to back up the rest of the home directories, simply change SOURCE back to /home rather than /home/trevor and it will work the way you intend.  Let us know how it works for you.

I'm afraid it hasn't worked for me.  It works and backs up if I am logged in, but it doesn't work if I am not logged in.  It doesn't even manage to mount Elrond.  The file tmp.log (as set up in crontab) is not created either, so I have no error log to help.

There's obviously something I've not done, or done wrong, but I'm stuck now.

Here's my crontab [COLOR="Red"]edit: this is in "trevor"'s crontab rather than root's - I thought that was necessary to trigger the decryption?[/COLOR]
```

MAILTO=""
SHELL=/bin/bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/root

# m h  dom mon dow   command
15 23 * * * /home/trevor/scripts/dailybackup > /home/trevor/scripts/cronerrors.log 2>&1
38 7-23 * * * /home/trevor/scripts/hourlybackup > /home/trevor/scripts/cronerrors.log 2>&1
42 * * * * /home/trevor/scripts/test >> /home/trevor/scripts/tmp.log 2>&1

```

Here's my sudoers file
```
Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias	BACKUP	= 	/home/trevor/scripts/hourlybackup, \
				/home/trevor/scripts/dailybackup, \
				/home/trevor/scripts/test

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# trevor is allowed to run backup scripts without a password
trevor	ALL	= NOPASSWD: BACKUP

```

and I used your code for the backup but put in as a script called test (which is referenced in the sudoers file and I set it with executable permissions of 755).  Here's the code
```

#!/bin/bash

# Backup script for the home partition of Thingol
# Written by Trevor Burton - April 22nd 2011
# Last modified by Trevor Burton - April 22nd 2011
# 
# Lots of help from the Ubuntu community
# http://ubuntuforums.org/showthread.php?p=10072677#post10072677
#
# this script is executed once per hour via the user trevor's crontab
# the user trevor needs to be in the sudoers file with 
# Cmd_Alias BACKUP = /home/trevor/scripts/hourlybackup (or whatever this script is called)
# trevor ALL = NOPASSWD: BACKUP
#

###############################################################
#
# First re-execute with sudo
# This ensures the encrypted home directory for trevor is decrypted for backup
# but still allows privileged use
# entries in the sudoers file allows this (see top)
#
###############################################################

if [ "$(id -u)" != "0" ]; then
  sudo "$0"
  exit $?
fi

###############################################################
#
# Normal Variables
#
###############################################################

BIN=/bin/

TREVOR=/home/trevor
LOGS=${TREVOR}/backup_logs

DATE=$(${BIN}date +%Y_%m_%d)
DATETIME=$(${BIN}date +%Y_%m_%d_%H%M%S)
HOUR=$(${BIN}date +%H)
LOGFILE=${LOGS}/hourly_${HOUR}_rsync.log

EXCLUDE=${LOGS}/rsync-exclude
SOURCE=/home/trevor
ELROND=/media/Elrond/
BACKUP=${ELROND}Backups/Thingol-Ubuntu/
TARGET=${BACKUP}hourly_${HOUR}/

###############################################################
#
# Write headers to the log file
#
###############################################################

echo "###" > $LOGFILE
echo "### HOURLY backup" >> $LOGFILE
echo "###" >> $LOGFILE;
echo "### Beginning rsync backup of $SOURCE" >> $LOGFILE;
echo "### to $TARGET" >> $LOGFILE;
echo "### on $(${BIN}date)" >> $LOGFILE;
echo "###" >> $LOGFILE;


###############################################################
#
# Next check that Elrond is mounted 
#
###############################################################

if ! mountpoint -q $ELROND; then
	echo "### Mounting Elrond at $DATETIME" >> $LOGFILE
	[ -d $ELROND ] || sudo mkdir $ELROND
	mount -t ntfs-3g /dev/sdb1 $ELROND 2>> $LOGFILE || { echo "Mounting of backup drives failed" >> $LOGFILE; exit; }
	echo "###" >> $LOGFILE
fi

echo "### About to backup up to $TARGET" >> $LOGFILE
echo "###" >> $LOGFILE

###############################################################
#
# Execute the hourly backup
#
###############################################################

rsync -av --progress --delete --log-file=$LOGFILE --exclude-from=$EXCLUDE $SOURCE $TARGET

```

---

### Post by Trevor Burton on 2011-05-08
Some positive progress ....

I moved the script and the exclude file out of my home directory into a new folder ( /scripts/ ).  I also set the backup logs to write to /scripts/backup_logs.

I want to backup /home/ (there are 4 other users with unencrypted drives).

It does backup, even when I am not logged in but the encrypted /home/trevor/ is encrypted on the target drive.

There are 2 files:
Access-Your-Private-Data.desktop
README.txt

The .desktop file is a link to 
/usr/bin/ecryptfs-mount-private
but unfortunately when clicked I get an error message 
> "Untrusted application launcher"
The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.
This seems to be a bug in eCryptFS.

I was rather hoping to get a decrypted backup.

I'm not sure what happens if I just try to backup 
/home/trevor
(or should that be /home/trevor/ ?)

I'll try.

Trevor

---

### Post by Dave_L on 2011-05-08
> **Trevor Burton said:**
> This seems to be a bug in eCryptFS.

I was rather hoping to get a decrypted backup.

(1) Are you logged in when the script is run?

(2) Does the script provide your login password or ecryptfs passphrase?  

If "no" to both (1) and (2), then ecryptfs is working properly.

---

### Post by Trevor Burton on 2011-05-08
> **Dave_L said:**
> (1) Are you logged in when the script is run?

(2) Does the script provide your login password or ecryptfs passphrase?  

If "no" to both (1) and (2), then ecryptfs is working properly.

I didn't mean ecryptfs was not working in general, just in respect of the backed up encrypted file not being able to be decrypted because the link is not "trusted".

See
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/586281]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/586281")

I think I am nearly there now.  I've moved the scripts and log files to a folder outside my encrypted home, I think I have the script backing up my encrypted home drive with no user logged in, and I'm experimenting to see if I can backup other users homes at the same time.

Trevor

---

### Post by Trevor Burton on 2011-05-08
Success!!

I moved the scripts and the rsync exclude file to a folder outside my home folder (/scripts).  I also directed log files there.

I rsynced my home folder alone, then each of my other users' home folders, followed finally by the /script folder (this was what I hadn't backed up when my previous system died!).

My encrypted home is backed up to a decrypted backup.
The other users non-encrypted homes are also backed up fine.

All working wonderfully.

Many thanks to all especially to trikster_x.

I think I might try to write a summary of all this in case anyone else is trying to do this, although I do realise that not everyone might want to make a decrypted backup of their encrypted home!

Trevor

---

### Post by Trevor Burton on 2011-05-09
Hmmm, got home after work and while yesterday's backups worked perfectly, today's are all encrypted still.  I'll keep investigating.

Trevor

---

### Post by Dave_L on 2011-05-09
Include the file /etc/mtab, or the output from the "mount" command, in the backup script.  If the encrypted directory is mounted, there should be a line similar to:

```
/home/USER/.Private on /home/USER type ecryptfs ...
```

---

### Post by Trevor Burton on 2011-05-09
> **Dave_L said:**
> Include the file /etc/mtab, or the output from the "mount" command, in the backup script.  If the encrypted directory is mounted, there should be a line similar to:

```
/home/USER/.Private on /home/USER type ecryptfs ...
```

Hi Dave,

I'm not sure what you mean by "include the file /etc/mtab in the backup script" 
There is a line just like your code in /etc/mtab, but how do I make that a command?
Do you mean try to mount the encrypted home folder within the script?

I can see why that might work, but last night I managed to get a decrypted backup without doing it, so I am now confused that a script that worked last night hasn't worked during today.

Trevor

---

### Post by Dave_L on 2011-05-09
Trevor:

I meant that the file /etc/mtab could be included as one of the files that is backed up.  That way you could easily check whether the encrypted directory was mounted (as an ecryptfs file system) at the time of the backup, which might be helpful for troubleshooting.

---

### Post by Trevor Burton on 2011-05-10
> **Dave_L said:**
> Trevor:
 
I meant that the file /etc/mtab could be included as one of the files that is backed up. That way you could easily check whether the encrypted directory was mounted (as an ecryptfs file system) at the time of the backup, which might be helpful for troubleshooting.
 
Right, that makes sense.  I'm guessing it won't be, but can't harm to check it.  Thanks for that.
 
I'm just flummoxed as to why a script that decrypted and rsynced my home folder on Sunday didn't decrypt it on Monday.
 
Trevor

---

### Post by Derek Karpinski on 2011-05-13
Trevor,

Please keep us posted. And if you get it working, post the scripts, and a short 'step by step' if you don't mind.  I'm actually trying to do this myself.

In my scenerio, I have two users with enycrypted /homes, and need to make backups to an external HDD.  I could live with encrypted backups as long as I can restore those backups easily.

---

### Post by Trevor Burton on 2011-05-15
> **Derek Karpinski said:**
> Trevor,

Please keep us posted. And if you get it working, post the scripts, and a short 'step by step' if you don't mind.  I'm actually trying to do this myself.

In my scenerio, I have two users with enycrypted /homes, and need to make backups to an external HDD.  I could live with encrypted backups as long as I can restore those backups easily.

Well, making the backups is straightforward, but at the moment, I can get them decrypted at the point of backing up.  I also am unsure how I would restore them in the event of a system crash for example.  I'm just about to post a script that doesn't quite work (!)

---

### Post by Trevor Burton on 2011-05-15
OK, progress so far.

My external HDD is not mounting (not sure why but I think it is a hardware fault) so I have now changed the rsync to work with a LAN based NAS device.  I've set up keys for the SSH so there are no passwords to worry about.  I know this can connect both manually and via scripts and I can execute commands over SSH, so that part of the script is OK.

Here is the remaining problem ...

[LIST=1]
[*]script fires up in trevor's crontab (trevor is the user with encrypted home directory)
[*]script re-runs itself under sudo
[*]if I am logged in script decrypts then backs up home drive of trevor 
[*]It then goes on and backs up the unencrypted /scripts folder (which trevor owns)
[*]if I am not logged in script backs up a couple of files in .cache, but nothing else (it made a link on the target drive when it was an external HDD but that didn't work)
[*]the script then goes on and happily backs up a normal copy of /scripts folder
[/LIST]

I *know* that at one point a similar script got a decrypted backup working, but it has stopped working and I don't know why.  Here is everything I think might be useful ...

[COLOR="DarkOrange"]THE SCRIPT (/scripts/test) [/COLOR]
```

#!/bin/bash
if [ "$(id -u)" != "0" ]; then
  sudo "$0"
  exit $?
fi

BIN=/bin/
LOGS=/scripts/backup_logs/
HOUR=$(${BIN}date +%H)
LOGFILE=${LOGS}hourly_${HOUR}_rsync.log

EXCLUDE=/scripts/rsync-exclude

BACKUPSERVER=admin@192.168.1.101:
BACKUPPATH=/volume1/NetBackup/Thingol-Ubuntu/

echo "###" > $LOGFILE
echo "### Here comes /etc/mtab" >> $LOGFILE
echo "###" >> $LOGFILE
echo "###" >> $LOGFILE
cat /etc/mtab >> $LOGFILE
echo "###" >> $LOGFILE
echo "###" >> $LOGFILE

SOURCE=/home/trevor/
DIRTARGET=${BACKUPPATH}hourly_${HOUR}/trevor/
TARGET=${BACKUPSERVER}${DIRTARGET}
ssh admin@192.168.1.101 "mkdir -p $DIRTARGET"
rsync -a --delete --log-file=$LOGFILE --exclude-from=$EXCLUDE $SOURCE $TARGET

SOURCE=/scripts/
DIRTARGET=${BACKUPPATH}hourly_${HOUR}/scripts/
TARGET=${BACKUPSERVER}${DIRTARGET}
ssh admin@192.168.1.101 "mkdir -p $DIRTARGET"
rsync -a --delete --log-file=$LOGFILE --exclude-from=$EXCLUDE $SOURCE $TARGET
```

[COLOR="DarkOrange"]THE CRONTAB for trevor[/COLOR]
```
MAILTO=""
SHELL=/bin/bash
PATH=/bin:/sbin:/usr/bin:/usr/sbin:/root

# m h  dom mon dow   command
55 * * * * /scripts/test > /scripts/cronerrors.log 2>&1
```

[COLOR="DarkOrange"]THE SUDOERS file[/COLOR]
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias	BACKUP	= 	/scripts/hourlybackup, \
				/scripts/dailybackup, \
				/scripts/test
# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# trevor is allowed to run backup scripts without a password
trevor	ALL	= NOPASSWD: BACKUP
```


[COLOR="DarkOrange"]The most recent log file[/COLOR] 
You can see how it tries to copy a link across to the NAS drive about mounting an encrypted private folder, but that doesn't actually get copied (unsurprisingly).  Also you can see that the encrypted drive is not mounted (even thought the script was originally called by user trevor), as it is not in /etc/mtab.
```

[COLOR="Red"]This is where the printout of /etc/mtab came - as you can see, the encrypted drive is not mounted[/COLOR]
###
### Here comes /etc/mtab
###
###
/dev/sda6 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda7 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/trevor/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=trevor 0 0
###
###
[COLOR="Red"]This is where the backup for /home/trevor started[/COLOR]
2011/05/15 15:02:02 [4303] building file list
2011/05/15 15:02:02 [4303] .d..tp..... ./
2011/05/15 15:02:02 [4303] cL+++++++++ .Private -> /home/.ecryptfs/trevor/.Private
2011/05/15 15:02:02 [4303] cL+++++++++ Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
2011/05/15 15:02:02 [4303] cL+++++++++ README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
2011/05/15 15:02:02 [4303] cd+++++++++ .cache/
2011/05/15 15:02:02 [4303] <f+++++++++ .cache/motd.legal-displayed
2011/05/15 15:02:02 [4303] cd+++++++++ .cache/gwibber/
2011/05/15 15:02:02 [4303] <f+++++++++ .cache/gwibber/gwibber.log
2011/05/15 15:02:02 [4303] cd+++++++++ .cache/wallpaper/
2011/05/15 15:02:02 [4303] <f+++++++++ .cache/wallpaper/zoom_1440_900__usr_share_backgrounds_warty-final-ubuntu.png
2011/05/15 15:02:02 [4303] sent 310548 bytes  received 94 bytes  total size 309944
[COLOR="Red"]This is where the backup for /scripts started[/COLOR]
2011/05/15 15:02:03 [4306] building file list
2011/05/15 15:02:03 [4306] .d..tp..... ./
2011/05/15 15:02:03 [4306] <f+++++++++ cronerrors.log
2011/05/15 15:02:03 [4306] <f+++++++++ dailybackup
2011/05/15 15:02:03 [4306] <f+++++++++ dailybackup.copyof
2011/05/15 15:02:03 [4306] <f+++++++++ hourlybackup
2011/05/15 15:02:03 [4306] <f+++++++++ hourlybackup.copyof
2011/05/15 15:02:03 [4306] <f+++++++++ minimal
2011/05/15 15:02:03 [4306] <f+++++++++ rsync-exclude
2011/05/15 15:02:03 [4306] <f+++++++++ test
2011/05/15 15:02:03 [4306] <f+++++++++ test.old
2011/05/15 15:02:03 [4306] <f+++++++++ ubuntupost
2011/05/15 15:02:03 [4306] cd+++++++++ backup_logs/
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/annual_2011_05_08_233002_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_08_233002_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_09_195001_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_09_203002_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_09_204001_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_10_204001_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_10_231501_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_11_231501_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_12_231501_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/daily_2011_05_13_231501_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_07_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_08_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_09_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_10_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_11_rsync.log
2011/05/15 15:02:03 [4306] <f+++++++++ backup_logs/hourly_12_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_13_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_14_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_15_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_16_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_17_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_18_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_19_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_20_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_21_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_22_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/hourly_23_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/monthly_2011_05_08_233002_rsync.log
2011/05/15 15:02:04 [4306] <f+++++++++ backup_logs/weekly_2011_05_08_233002_rsync.log
2011/05/15 15:02:04 [4306] sent 11648454 bytes  received 761 bytes  total size 11642085
```

Any ideas?

---

### Post by trikster_x on 2011-05-15
Okay, well, from my previous testing, I can tell you that the link and readme.txt that are created happen when an unauthorized user attempts to decrypt your encrypted directory, so that is where your problem now lies.  For some reason, the script is not supplying the necessary information to decrypt your home directory.  I'll do some testing and see if I can figure out how to get it to work the way you want.

EDIT:

Here is what I have found for my install:

1.  Backup runs as intended while logged in.
2.  Backup runs as intended while not logged in as long as a previous successful login occured since most recent reboot.
3.  Backup does not run if there is no previous successful login since most recent reboot.

I don't have access to any of my home machines right now, so I can't test the ssh aspect.  This is where it gets difficult to troubleshoot without physical access to the machine.  My suggestion is to start eliminating as many variables as possible, then reintroduce them one at a time until you find the cause of the problem.  If it were my machine I would do the following:

1.  Rewrite the script to work as simply as possible.  Meaning remove the necessity of mounting any drives.  Make it so the only thing the script is attempting to do is run the backup of the encrypted directory and make your logs.  Make it so the backup writes to your encrypted directory, and try to keep the script and log files within the encrypted directory as well.  Start with being logged in, then log out, then restart without login to see if you need to log in after a restart for it to run properly or at all.  Once you have determined the nature of the script and crontab, add a bit of complexity.

2.  See if the backup will successfully write to an unencrypted directory.  Again; logged in, logged out, restart without login.

3.  Use the script to check for a hdd, and if not present mount, and run the backup.  Logged in, logged out, restart without login.

4.  Now add your SSH bit and see how that interacts.  Again; logged in, logged out, restart without login.  

Obviously the above is only a set of suggestions, as you will need to change it depending on how you are going about your backup.  Once you have found the failure point, then post it if you aren't able to figure out how to address the problem yourself, and we can probably offer more help.  As it is, there are just too many things going on in your script to point at something and say that is your problem without getting on your machine and trying some things.

---

### Post by Trevor Burton on 2011-05-15
> **trikster_x said:**
> Okay, well, from my previous testing, I can tell you that the link and readme.txt that are created happen when an unauthorized user attempts to decrypt your encrypted directory, so that is where your problem now lies.  For some reason, the script is not supplying the necessary information to decrypt your home directory.  I'll do some testing and see if I can figure out how to get it to work the way you want.

EDIT:

Here is what I have found for my install:

1.  Backup runs as intended while logged in.
2.  Backup runs as intended while not logged in as long as a previous successful login occured since most recent reboot.
3.  Backup does not run if there is no previous successful login since most recent reboot.

....

Ahh, now that is looking like it makes some sense to me (item 3 that is). I had an idea that it worked the day I set it up, but not the following day - perhaps because I did not log in before the first backup kicked off the following day.

Thank you for helping - it looks like there might be a way around this so I'll try your suggested reintroduction of more complicated elements from a very basic script.  That will take me some time though - I've started a new job and I'm really busy at work.

Many thanks for taking the time to help me!

I'll report back.

Trevor Burton

---

### Post by trikster_x on 2011-05-15
One last suggestion:

Outline how you want the script to act from beginning to end, since it seems the script has gone through 2 or 3 iterations since you started this thread.  Not only does it help you to keep on track and minimize your script,it helps if everyone knows exactly what you are trying to accomplish when they are helping you.  If you decide you want to add, remove, or otherwise modify a behavior, post what you wish the end result to be.  My guess is that your SSH bit is probably what is causing the problem at this point, since you have had the script working correctly in the past.  But that is just a guess at this point.  Good luck to you and keep us posted.

---

### Post by Dave_L on 2011-05-15
This may be relevant: [Encrypted home directory readable after logout](https://answers.launchpad.net/ecryptfs/+question/152141)

Through my own experimentation, I've found that sometimes the private directory gets unmounted when logging off, and sometimes it doesn't.

I'm using Ubuntu 10.04.  According to that article, the behavior may have changed in 10.10 or 11.04.

---

### Post by trikster_x on 2011-05-15
> **Derek Karpinski said:**
> Trevor,

Please keep us posted. And if you get it working, post the scripts, and a short 'step by step' if you don't mind.  I'm actually trying to do this myself.

In my scenerio, I have two users with enycrypted /homes, and need to make backups to an external HDD.  I could live with encrypted backups as long as I can restore those backups easily.

You would likely be able to use the script that was used halfway through this thread, but you will have to run the script in the crontab of any users with an encrypted directory you want to back up, otherwise you will not be allowed access for mounting the directories.  That means using two separate scripts and modifying them to use your file hierarchy.  You'll also need to make sure each encrypted account gets logged in after every reboot.  

A simple cron job using the "@reboot" option can insure one of the accounts logs in and out automatically at startup, but it's not the most secure method, since you have to authorize automatic login for the account, and it will be logged in for a few seconds while the command runs.  If you're interested in this method, I can explain in a bit more detail.

@Dave_L:

That's an interesting read.  I'll have to test that more extensively a bit later.  Good to see they addressed the issue in the 11.04 release.  Not sure of the effect it will have on this script, since we are not su-ing from a different user, but allowing a user's own crontab to access the encrypted directory.  But it is very possible that this script would not work at all unless logged in to the account when it is run in 11.04 and later.

---

