---
title: "rsync problem with crontab"
date: 2009-12-04
forum: General Help
---

### Post by midfel11 on 2009-12-04
I've got a backup shell script that uses rsync to backup my data to a NAS.  If I run the script from the command prompt (as root) it works.  I added a crontab entry for root to run the script.  The script runs and the rsync starts, but consistently runs into this error while building the file list:[INDENT][FONT=Courier New]2009/12/03 21:00:07 [17343] building file list
.
.
.
2009/12/03 22:52:02 [17635] rsync error: errors with program diagnostics (code 13) at log.c(237) [sender=3.0.6][/FONT]
[/INDENT]Here is the content of my backup script, backup.sh:[INDENT][FONT=Courier New]#!/bin/bash

# Backup data to the Synology share via rsync
rsync --password-file=/root/synology.passwd --log-file=/var/log/rsync/rsync_$(date +%Y%m%d).log --archive --delete --compress /etc /root /home admin@192.168.0.11::NetBackup/sonata/[/FONT]
[/INDENT]Here is the crontab entry:[INDENT][FONT=Courier New]# m h  dom mon dow   command
52 22 * * * /root/backup.sh[/FONT]
[/INDENT]Any ideas what may be different between running this in cron and from the command line?

---

### Post by midfel11 on 2009-12-10
Bump.....still haven't found a solution yet.

---

### Post by undoIT on 2010-05-19
Although I have a different script and method, I am having the exact same problem. If I run the script manually in terminal, it works perfect every time. However, the crontab for the script doesn't. The strange thing is that sometimes after fiddling around with stuff for a long time, the crontab finally works. I test it a few times in a row and it works. So I think all is set and dandy. But then, the next day it stops working.

In my case, the crontab works for all of the . folders, i.e. .mozilla, .local, but it skips Documents, Pictures etc. Really frustrating and hard to figure out what is going on.

---

### Post by undoIT on 2010-05-19
I think I may have FINALLY solved this. It appears that there is either a bug in rsync, or the archive setting is causing the failure. I just did two successful runs from crontab by replacing the archive command. Perhaps it is the -D command that is included with archive mode.

For your script, try replacing --archive with -rlptgo

Of course the true test will to see if it is still working tomorrow at noon after a reboot.

---

