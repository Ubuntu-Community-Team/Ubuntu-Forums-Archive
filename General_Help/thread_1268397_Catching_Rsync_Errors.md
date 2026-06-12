---
title: "Catching Rsync Errors"
date: 2009-09-16
forum: General Help
---

### Post by jimjawn on 2009-09-16
Hey All,

I've recently started using jungledisk in combination with rsync to backup my files and I love it!  I have a backup.sh script with the rsync command that I run via cron each night.  However, I've found that sometimes, an error occurs either with the jungledisk daemon or my internet connection goes out and I don't realize it for a few days.  

Instead of checking each night to see if it sync'd up, I'd like to trap any errors that occur during the rsync.  I don't want successful emails, just errors.

I've done some simple bash scripting but I'm not sure how to go about checking for errors from the rsync command.  Can anyone point me in the right direction?  I know this involves grabbing the output from stdin/stdout but I'm not sure where to start.

Perhaps an explanation of these two lines:

```
rsync -az -e ssh --delete $HOSTTOBACKUP:$SOURCE $DR_BACKUP_DIR/daily.0 > $tempfile 2>&1
if [ $? -eq 0 ]

```
Thanks,

Jim

---

