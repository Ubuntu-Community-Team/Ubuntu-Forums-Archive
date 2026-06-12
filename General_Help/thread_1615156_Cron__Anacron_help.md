---
title: "Cron / Anacron help"
date: 2010-11-06
forum: General Help
---

### Post by NathanScrivener on 2010-11-06
Hi, I've been trying to get my head around cron / anacron and finding it very perplexing .... so hopefully somebody here would be kind enough to help me with my situation :-)

I have some files on a web-host, and I wish to backup the files daily. I have SSH enabled and have managed to follow the directions to get the public/private key share working so no password is needed :-)

So first I need to issue a command through SSH to dump my databases, so they can be backed up. 

Then I need to mirror the files using RSYNC to my desktop PC over SSH.

Finally I need to run RDIFF-backup on the mirror, to save incremental changes to the files. This results in a duplicate copy, but as the web-host server doesn't have RDIFF-backup installed I need to do it this way. 

So, these are the commands I need to run:

```
ssh xxxx@xxxxx.com "mysqldump --user=xxxx --password=xxxx xxxx > ~/database-dump/xxxxsqlbackup.sql"

rsync -a --delete -e ssh xxxx@xxxxx.com:~/ ~/bluehost-mirror

rdiff-backup ~/bluehost-mirror ~/bluehost-mirror-rdiff-incremental
```

This needs to run daily, and as this will run from my desktop PC, the logic needs to be 'run daily at 6am or whenever the computer is next turned on' - or something thereabouts. This is the bit I am stuck on. Also, I am unsure of what user-level issues I may encounter - will the script run as my user, or as root, do I need to be logged in as my user for it to work, etc???

Thanks very much :-)

---

### Post by Barriehie on 2010-11-06
Make those commands into a script: (Don't forget to make it executable, i.e. chmod +x <path_to_script>/<script_name>) Might have to be root to do this depending on where you put it.

```

#!/bin/bash
ssh xxxx@xxxxx.com "mysqldump --user=xxxx --password=xxxx xxxx > ~/database-dump/xxxxsqlbackup.sql"

rsync -a --delete -e ssh xxxx@xxxxx.com:~/ ~/bluehost-mirror

rdiff-backup ~/bluehost-mirror ~/bluehost-mirror-rdiff-incremental

exit 0
```

and add this line to your /etc/crontanb file:

```

0 6 * * * root <path_to_script>/<script_name>
```

Script should probably go in /usr/local/bin
(will have to be root to put it there and chmod it to executable)

Edit: If you run it from /usr/local/bin/ then the crontab user will have to be root and if you run it from /home/your_username/bin/ then your_username can be the crontab entry user.

---

### Post by trikster_x on 2010-11-06
Barriehie's crontab entry syntax is spot on for running the script every day at 6, but as far as running it at login if you missed a backup cycle, that would require a bit more BASH magic.  You'll have to program another script to run at reboot that looks at the timestamp on the backup file and compares it to the current time to see if you missed a backup cycle.

---

### Post by Barriehie on 2010-11-06
> **trikster_x said:**
> Barriehie's crontab entry syntax is spot on for running the script every day at 6, but as far as running it at login if you missed a backup cycle, that would require a bit more BASH magic.  You'll have to program another script to run at reboot that looks at the timestamp on the backup file and compares it to the current time to see if you missed a backup cycle.

BASH magic, I like that. :)  How about after the backup is completed for the day then the last line before exit is:
```

touch <some_path>/$(date +%m%d%y)
```This creates a file say in /home/username/jobs that is mmddyy.  Somewhere in $HOME/.bashrc 
```

if [ ! -e /home/username/jobs/$(date +%m%d%y ]
   run backup routine
fi
```

I think I thought that right...
Edit: Oops, if you reboot B4 6 then the backup will run so the backup script will have to make the same check... or else just let it overwrite the earlier backup...

Hmm, have to nuke the old files so that would be a find thing:
```

find /home/user_name/jobs -name ?????? -mtime +1 | xargs rm
```

---

### Post by efflandt on 2010-11-06
If you do **crontab -e** as your own user, it will run as you.  If you **sudo crontab -e** that would edit root's crontab.

In either, case assume that there is nothing in the environment of anything run from cron (including PATH).  So it is best to either define PATH or use full paths for everything.  And the shell might be dash instead of bash, so "~" might not work in a path (best to assume it does not).

Missing environment is why many people ask why their script works from a terminal and not from cron.

---

### Post by Barriehie on 2010-11-06
> **efflandt said:**
> If you do **crontab -e** as your own user, it will run as you.  If you **sudo crontab -e** that would edit root's crontab.

In either, case assume that there is nothing in the environment of anything run from cron (including PATH).  So it is best to either define PATH or use full paths for everything.  And the shell might be dash instead of bash, so "~" might not work in a path (best to assume it does not).

Missing environment is why many people ask why their script works from a terminal and not from cron.

Good point, always best to include full paths!

---

### Post by trikster_x on 2010-11-06
```
#! /bin/bash
last_backup=`stat -c %Z ~/bluehost-mirror-rdiff-incremental`
current_time=`date +%s`
hours_since_backup=$((($current_time - $last_backup)/3600))
if (($hours_since_backup>=24))

   then ssh xxxx@xxxxx.com "mysqldump --user=xxxx --password=xxxx xxxx > ~/database-dump/xxxxsqlbackup.sql" && rsync -a --delete -e ssh xxxx@xxxxx.com:~/ ~/bluehost-mirror && rdiff-backup ~/bluehost-mirror ~/bluehost-mirror-rdiff-incremental

fi
```

Just something I worked up to check for the timestamp on the actual backup file and proceed with the backup if it has been at least 24 hours since the last backup.  Save this in a seperate file from the original script, since it will not work right running it on a timer as written, then toss this in crontab to run it at reboot:

```
@reboot /path/to/script
```

And like magic the script runs at every reboot and performs the backup only when necessary.

---

### Post by NathanScrivener on 2010-11-06
Wow, my head is spinning! You guys are rock-star with this stuff! :guitar:

So if I were to take the script format in trickster_x's last post, am I right to assume that I should put it in crontab to run at reboot, plus an additional entry to run the exact same script every day at 6am? So therefore if the machine is left running, it will trigger the script also, but it will never run more than once in a 24 hour period?

---

### Post by Barriehie on 2010-11-06
@trikster_s:
Use of stat is pretty cool!  I've only used it to look at mtimes.  Learned something again!

---

### Post by NathanScrivener on 2010-11-06
Sorry, just noticed you said:

>  Save this in a seperate file from the original script, since it will not work right running it on a timer as written

I'm a bit confused by this, wouldn't it run max once every 24 hours?

[EDIT] - click! light-bulb just went on. Needs to be without 'if' when run every 24 hours, then the one with the 'if' will only run if the first one is missed. This keeps a consistent time for running the backup, wherever possible.

---

### Post by NathanScrivener on 2010-11-06
OK, so this is a summary:

I now have two scripts, one labelled 'backup-bluehost-daily' and the other 'backup-bluehost-reboot-check'. The daily script runs every day at 6am, so, will always run a backup if the machine is on at this time. The reboot check script runs at every reboot, and checks the filestamps - if it has been more than 24 hours since the last backup, the machine must have been off at 6am, therefore the backup was missed. Proceed with missed backup.

Full paths have been used for the local paths, so that there is no issue with the cron environment. (May I assume that the paths referenced in the SSH commands can keep the ~?)

Scripts are located in /home/user/bin/ and have been marked executable.
Crontab entries have been placed in user crontab. (I used the command crontab -e to access the editor). 

backup-bluehost-daily looks like this:

```
#!/bin/bash

ssh user@xxxx.com "mysqldump --user=xxx --password=xxx database  > ~/database-dump/xxxsqlbackup.sql" 
rsync -a --delete -e ssh user@xxxx.com:~/ /home/user/bluehost-mirror 
rdiff-backup /home/user/bluehost-mirror /home/user/bluehost-mirror-rdiff-incremental

exit 0
```

backup-bluehost-reboot-check looks like this:

```
#!/bin/bash

last_backup=`stat -c %Z /home/user/bluehost-mirror-rdiff-incremental`
current_time=`date +%s`
hours_since_backup=$((($current_time - $last_backup)/3600))

if (($hours_since_backup>=24))

then ssh user@xxxx.com "mysqldump --user=xxx --password=xxx database  > ~/database-dump/xxxsqlbackup.sql" && rsync -a --delete -e ssh user@xxxx.com:~/ /home/user/bluehost-mirror && rdiff-backup /home/user/bluehost-mirror /home/user/bluehost-mirror-rdiff-incremental

fi

exit 0
```

---

### Post by trikster_x on 2010-11-07
Those both look good.  Might I suggest, though, taking advantage of cron's logging capabilities?  All you have to do is make your crontab entry look like this:
```
@reboot /path/to/script >> /path/to/log/file.log 2>&1
```
The ">> /path//to/log 2>&1" is a simple little addition to any cron entry and will send any of the stdout as well as the stderr to your log file for any future troubleshooting you may have to do.

---

### Post by NathanScrivener on 2010-11-07
Great, thanks for that! Doing that was the next thing I wanted to figure out!

One more question, what happens if the machine is in sleep mode at the scheduled time? It may not be shut down completely, is there a cron command to run on resume from sleep?

---

### Post by Cheesehead on 2010-11-07
If your system is suspended/sleeping/hibernating, cron won't be running. Your system won't do the operation.

The more events (time, startup, wakeup) you add, the more complex  your scripting will be, and the more maintenance you will need to do in it in the future - so be sure to put a lot of useful comments in! How important is it really that the backup be as close to 24 hours as possible at a certain time?

You can do it with just an anacron job. Anacron runs at startup and resume, too. For more complex criteria, you can have Upstart trigger your scripts upon startup or resume (or network up or whatever)

If you're choosing an off-peak time because you don't want a performance hit while you're using your system, it might be easier to simply set the process 'nice' level to something you won't notice running in the background during your workday. Nice is a great thing.

---

### Post by trikster_x on 2010-11-07
You can try placing the script in /etc/pm/sleep.d, scripts there are supposed to run on wake from sleep, but I have never tried so I don't know for sure.  You won't have the benefit of the log file unless you put it directly in the script.  It's not hard, you just have to add the
```
>> /path/to/log 2>&1
```
to the commands you want to record the output from.  You'll want to use the reboot script as your template.  

I think I should also mention a bit about the way you write out the logging portion:  

Using ">>" will create a log file if it doesn't exist and append the end of a log file if it does exist.  That means you will have to manually delete the old portions of the file or set another cron job to delete the log file every now and then.  In my cron jobs, I keep track of the different sections by throwing a simple date command at the beginning of the script.

Using ">" will create a log file if it doesn't exist and overwrite the log file if it does exist.  I tend to shy away from this just because of the fact that I like to have at least a small history to look back on my cron jobs in case I miss a cycle or two.  You could also modify the log's filename to include the creation date, but on a daily cron job, you could start to amass a large number of logs in a short time.

Using "2>&1" is the part that pipes the stdout and stderr to your log file.

---

### Post by NathanScrivener on 2010-11-07
Thanks for the continuing useful comments. A further potential flaw in the 'reboot' script - my desktop computer connects wirelessly, the script could run prior to the establishment of the wireless connection, which would cause it to fail.

This leads to me think that I need to do the following;

1. Change the 'stat' command to reference the mirror folder, not the rdiff folder, as the date-stamp on the mirror folder won't change if rsync failed to connect. But rdiff-backup could run as it is local and without testing I suspect it could change the time-stamp.

2. Instead of running the 'bluehost-backup-reboot-check' script on reboot, just set it to run every hour. Most of the time it will simply abort, rather than run the backup, and I can't see the resource overhead of doing this as significant. 

OR

Do the whole thing with Anacron as indicated above, which I suspected may be a good way to solve this requirement, hence me referencing this in the thread title.

As I don't know anything about Anacron, it would be interesting to see how this would resolved using it.  According to [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto"), Anacron is run on every startup, wake-up (is this only on laptops?), plug-in (is this only on laptops?), and at 7.30am every day.

---

### Post by Cheesehead on 2010-11-07
To use anacron:

First, look in /etc/anacrontab to see when anacron really runs daily. For example, mine runs at 6:25 am (if the system is awake), not 7:30.

Second, put your script into the /etc/cron.daily directory.



However, if you're running from a laptop (so network-up is an additional condition), then you really have two conditions:

If more than 24 hours have elapsed, AND if the network is up, 
Then run the script.

For example, if your script logs the action (to syslog or a custom log)
then you can use Upstart to catch the network-up signal and trigger your script.
Your script checks for a previous log entry (with timestamp) and determines if backup is necessary, conducts the backup, and logs the result.
This has the additional benefit of capturing any backup failures in the log.



Capturing the network-up signal using upstart:
Simply place the following file (my-network-up.conf) in /etc/init.
Obviously, you an customize the filename, script paths, descriptions, etc.
```
# 'network-up.sh' - capture the network-up signal and start my custom scripts.

description "start my custom scripts when the network comes up"

start on net-device-up

script
exec /home/path/to/my/script_1.sh
exec /home/path/to/my/script_2.sh
exec /home/path/to/my/script_3.sh
end script

```

The script will be active upon next restart, or use the following useful commands
```

sudo initctl reload-configuration      # Reload Upstart configs immediately
sudo initctl emit net-device-up        # Optional. Send the net-device-up signal manually. Great for testing!

```

---

