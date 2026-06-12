---
title: "crontab not running"
date: 2009-10-08
forum: General Help
---

### Post by dmatusow on 2009-10-08
I have looked through the posts on crontab. I had a test message showing up in /var/log/syslog, so I know that things were atleast partially working. Now...nothing.
 
I have a simple script referenced in my personal crontab (crontab -e). The crontab entry is:
 
0 2 * * * * /home/david/rsync-backup >> /home/david/log/rsync-backup.log
 
The script is 
 
#!/bin/sh
RT=`date`
rsync -avruogtEph --progress --stats /backup1/ /backup2/backup1/ 
echo "rsync-backup ran" $RT >> /home/david/log/rsync-backup.log
 
I can run the command from the command line and I see the entry in the log. I also placed a dummy into cron.daily. This was set to only output a simple echo to the log.
 
NEITHER of these seem to be running. Why?? :(
 
I created /etc/cron.allow and put my ID in. Just to make sure, I removed /etc/cron.deny.
 
Thanks

---

### Post by slakkie on 2009-10-08
Set the PATH inside your script. Once you run from cron it will not have your env variables, so setting a PATH and other env. variables are needed.

---

