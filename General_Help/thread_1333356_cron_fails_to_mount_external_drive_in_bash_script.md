---
title: "cron fails to mount external drive in bash script"
date: 2009-11-21
forum: General Help
---

### Post by chu_ben on 2009-11-21
I have a backup script that the root user runs with a cron job.  If I execute the script manually using 'sudo', then it runs fine.  It just fails when cron runs it.  It used to run fine in Jaunty Jackelope.  What might be wrong with my script?  Here are the relevant lines:

```
backupdevice=$(/sbin/blkid -l -t LABEL="Backup" -o device)
/bin/mount $backupdevice -t ext4 /media/Backup \
  || { echo "  * Error mounting external drive." \
  >> $logfile; exit 1; }
```Thanks in advance for any help solving this!

---

