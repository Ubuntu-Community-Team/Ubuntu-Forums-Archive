---
title: "Cron Ignores Bash Script Variables"
date: 2011-05-04
forum: General Help
---

### Post by mangy_mathan on 2011-05-04
I have a personal server and a dynamic IP address, so I wrote a script to check the currently assigned IP address and compare it to the one stored in a file from the last check, and visit the update URL if it's different.

The script is below.

```
#!/bin/bash
 
# These variables are established during setup. They can be changed here if you so choose.
iface=eth1
 
updateadd=http://freedns.afraid.org/dynamic/update.php?XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 
location=/etc/freedns
 
 
# Poor man's daemon.
while true; do
 if test -e $location/ipcurrent.conf
   then
   CacheIP=$(cat $location/ipcurrent.conf)
 fi
 # It slices, it dices, it extracts the current IP address from the interface output.
 TrueIP=$(ifconfig $iface | grep "inet addr" | cut -d: -f2 | cut -d" " -f1)
 if [ "$TrueIP" = "$CacheIP" ]
 then
   # The current and cached IP are the same, so no update.
   echo 'Update not required.'
 else
   # The IP has changed, so update accordingly.
   echo 'Updating DNS to '$TrueIP
   wget $updateadd -o /dev/null -O /dev/stdout
   echo `date`'IP changed to '$TrueIP >> $location/ipcurrent.log
 fi
 echo $TrueIP > $location/ipcurrent.conf
 sleep 30
done
```

If ran manually, it works properly, regardless of whether or not I'm in its current working directory. If ran as a cronjob, however, it appears to forget the variables immediately. The ipcurrent.conf file becomes blank, and the ipcurrent.log file shows that the "IP changed to " with nothing followed. The DNS entry does not update, indicating that it has apparently forgotten the URL as well.

The cron entry is
```
@reboot sh /etc/freedns/dnsupdate.sh
```
but it has the same result if sh is replace with /bin/bash. I have a second script meant to send the HTTP access logs to me, which is also not working properly, so perhaps it's something to do with the script or syntax that I'm missing?

---

### Post by Habitual on 2011-05-04
Try this on line 1:
```
#!/usr/bin/env bash
```
instead of 
```
#!/bin/bash
```

---

### Post by mangy_mathan on 2011-05-04
Thanks for the suggestion, but it didn't change anything. Both scripts behave just as they did with #!/bin/bash.

I probably should have mentioned, these are running under the root crontab, not mine. I suspect that makes a difference.

---

### Post by DaithiF on 2011-05-05
Hi,
most likely its the path to ifconfig -- this is located in /sbin but cron's default PATH is /usr/bin:/bin, so the command won't be found when run under cron.

so:
1. use an explicit path to ifconfig, ie. /sbin/ifconfig
2. more generally, when debugging cron jobs that don't run, you have 2 choices, either (a) stare at the script and guess whats going on when cron runs the job, or (b) capture the output of the job as cron runs it, so that you can see whats actually going on :)
hint: (b) is usually easier!
so add** > /path/to/some/logfile 2>&1** to the end of the crontab line to capture stdout and stderr output to a logfile somewhere and inspect that logfile afterwards.

Note that if you have mail set up on your machine (b) is unnecessary because cron will mail the output to the cron user thats running the job, but (1) ubuntu desktop doesnt' have an MTA installed by default, so this doesnt' happen, or (2) even if mail is set up, many people no longer know about or check their user's mail accounts, so the logfile approach above is often easier.

---

### Post by mangy_mathan on 2011-05-05
Thanks! That was the problem. Both ifconfig and sendmail were in an sbin folder. Specifying the full path made them functional. I'll remember that from now on.

---

