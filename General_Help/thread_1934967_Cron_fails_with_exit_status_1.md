---
title: "Cron fails with exit status 1"
date: 2012-03-03
forum: General Help
---

### Post by kakaboeie on 2012-03-03
Been fighting this one for over one and a half hour now.. can't figure it out.

Cron doesn't execute it's commands. To test if it was my shell script I even added a really simple cron (make a directory), that also doesn't work.

**crontab -l reports:**

* * * * * /var/bashes/backup_codeblocks.sh 2>&1 >> /var/bashes/logs/backup_codeblocks.log
* * * * * sudo mkdir /var/testard

**backup_codeblocks.sh**:

```
#!/bin/bash
cd /home/henk/Documents/
date=`date +%Y-%m-%d_%R`
sudo tar cvpzf /var/backups-manual/Codeblocks_$date.tgz --exclude=*/bin Codeblocks
```/var/bashes folder is chmodded 777
 /var/backups-manual is chmodded 777
backup_codeblocks.sh is chmodded u+x and works fine when run manually.
 The cron does create the backup_codeblocks.log file but it's empty.
[B]
/var/log/syslog[/B]:

```
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7277]: (henk) CMD (/var/bashes/backup_codeblocks.sh 2>&1 >> /var/bashes/logs/backup_codeblocks.log)
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7278]: (henk) CMD (sudo mkdir /var/testard)
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7275]: (CRON) error (grandchild #7278 failed with exit status 1)
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7275]: (CRON) info (No MTA installed, discarding output)
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7276]: (CRON) error (grandchild #7277 failed with exit status 1)
Mar  3 14:40:01 henk-HP-G62-Notebook-PC CRON[7276]: (CRON) info (No MTA installed, discarding output)
```

What gives?

---

### Post by TheFu on 2012-03-03
Often cron failures are due to environment issues.  For security the environment that cron provides is not the same as the user's environment.  There is an easy fix that also happens to be a best practice for all scripting.

**Always provide the full path to any external commands inside your scripts.**

'tar' should be /bin/tar (at least on my system) and 'date' is /bin/date. Your specific locations may be different.

Lastly, you didn't actually verify that that the 'cd' command worked. You could be in any directory.  What happens if that directory doesn't exist?

With bash scripting, you may want to enable stop on error, noclobber, and catch any signals.

Ok, with all that said, I looked at your errors and cron wants to send an email out when it finishes. That means you need an MTA like postfix installed.  That is the MTA error.

---

### Post by kakaboeie on 2012-03-03
Thanks for your tips. I figured out how to fix it though. Rather than editing my own users crontab (crontab -e) I should have been editing **sudo crontab -e**. It works now ;)

---

### Post by kevdog on 2012-03-03
I don't think you really need to install a MTA if you don't want something mailed to you.  You could just redirect the output from your commands into something called a "bit bucket" which means the output is dumped into a big black hole never to be seen again -- it suppresses any output of errors.

This could be done by adding:
>/dev/null 2>&1

to the back of each of your command lines.  

Further explanation could be found here: [http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/](http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/)

Basically the > /dev/null states redirect STDOUT to nothing (/dev/null) 

The 2>&1 means redirect STDERR to STDOUT (which in turn is redirected to /dev/null).

As far as the other advice given in this thread -- USE IT!! Always use absolute paths in a cron script since cron scripts run in very limited environments -- image they don't have a $PATH statement or any environment variables.

---

