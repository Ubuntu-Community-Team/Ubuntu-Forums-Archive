---
title: "Rsync script of multiple tasks"
date: 2012-03-21
forum: General Help
---

### Post by fisheater on 2012-03-21
Hi all,

It has taken a long time, but I have finally prepared my first .sh script.

Problem: it is a rsync task that contains 3 lines. Only the first seems to be running, then the next two are not completed.

Example, named rsync-shell.sh in root:
```
#!/bin/bash
# Personal backup, multiple targets
# deleted from command --exclude="FreeNAS*"
rsync -av --delete --exclude ".*" --exclude="Downloads"  /home/stonecutter/ /media/2nd_HD/stonecutter_backup
rsync -av --delete --exclude ".*" --exclude="Downloads" /home/stonecutter/ /mnt/NAS/Backup/Backup_Personal
rsync -av --delete --exclude ".*" --exclude FreeNAS/Videos /mnt/NAS /media/2nd_HD/emergency_backup
```

Solutions?

Issue two:
Setting this up as a daily cron job. 
My first setup seems to have filed.
1. Sudo crontab -e
2. 0 23 * * * /root/rsync-shell.sh
3. nothing happens

From what I have read:
1. i should be using: crontab -e (no sudo)
2. fix the rsync-shell.sh problem noted above
3. where does crontab.allow come in?

Thanks in advance!

FE

---

### Post by Paqman on 2012-03-21
Do the other lines work ok if you run them individually? I would strongly advise you to add some lines to the script that check that the target mountpoints are actually mounted before starting the rsync. Otherwise it'll dump your backups onto your local drive (which can clog it up very quickly).

Regarding cron, the easiest thing to do is drop the whole script into /etc/cron.daily, mark it as executable and relax. Besides avoiding all the hassle of messing with crontab, doing it this way also has the advantage that if the machine is turned off some of the time it'll still get run once a day.

---

### Post by fisheater on 2012-03-21
Do the other lines work ok if you run them individually? 
- yes, I tested them.

One unexpected problem with my .sh was that it is run as root and now I am having permission problems with the files copied with the script.

I like your idea of /etc/cron.daily. I have not yet read about this and will look into how to do it.

Thanks for your reply.

FE

---

