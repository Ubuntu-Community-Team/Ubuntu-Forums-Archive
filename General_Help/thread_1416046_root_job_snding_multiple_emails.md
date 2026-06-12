---
title: "root job snding multiple emails"
date: 2010-02-25
forum: General Help
---

### Post by Bartly on 2010-02-25
I have an rsync backup job scripted and run by cron at 12:00 every day. It emails me the log from rsync. The problem is that it sends the same email every minute starting at 12:00 and ending at 1:00. I can't figure out what I did to cause this. It is not happening on my other ubuntu server. 

```
# m h  dom mon dow   command
 * 12 * * 1,2,3,4,5 /home/barry/bin/backup.sh > /dev/null
``````
 #!/bin/sh
rsync -aut /usr/share/library /mnt/backup/WordPress > /home/barry/backup.log
rsync -aut /usr/share/materials /mnt/backup/WordPress >> /home/barry/backup.log
rsync -aut /usr/share/discussions /mnt/backup/WordPress >> /home/barry/backup.log
mail bsmith@xxlo.com < /home/barry/backup.log
```By the way, I know this is a very simple script, I am  new to shell scripting but it seems to work fine as far as the backups go.

---

### Post by gmargo on 2010-02-25
That first asterisk in the crontab entry is the minute field, so it runs on every minute.  Set that field to 0 and it will run only at 12:00.

---

### Post by Bartly on 2010-02-25
> **gmargo said:**
> That first asterisk in the crontab entry is the minute field, so it runs on every minute. Set that field to 0 and it will run only at 12:00.
 
Oh good grief! Don't you just love newbs? Thanks.

---

