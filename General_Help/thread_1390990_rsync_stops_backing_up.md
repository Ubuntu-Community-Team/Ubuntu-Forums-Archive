---
title: "rsync stops backing up"
date: 2010-01-26
forum: General Help
---

### Post by lsutiger on 2010-01-26
I am using the following command to backup my data:
```
rsync -arvu /home/ /mnt/backup/9.10/
```
/mnt/backup/9.10 is a network drive that I mount in fstab at bootup and is accessible.
I have this running everyday @ 10pm.
I was not backing up correctly so I send the stout to a log. Attached is the log. If you notice it stops brian/.cache/

The log is about 3 days worth. Could someone clue me in on what

---

### Post by llawwehttam on 2010-01-26
It might be that you don't have permissions. Just a guess but have you tried running as sudo. Also try the --progress as then you can watch it go.

EDIT: try the n option as well then you can give it a dry run in terminal and see if it gives any errors.

---

### Post by lsutiger on 2010-01-26
I am running it as me right now and it seems to be doing fine. The permissions are 777 on the backup mount.
The log is from running it from cron (scheduled tasks) and that is when it has a problem.

Thank you for the input.

---

### Post by lsutiger on 2010-01-27
I tried as sudo and let it run last night. I removed the previous backup as it had errors.
When I walk in this morning, the backup finished, but when I go to view the files, it did not copy any of the files, just the directory structure.???

Here's the code again:
```
rsync -arvu /home/ /mnt/backup/9.10/
```

---

### Post by lsutiger on 2010-02-03
Bump

---

### Post by john newbuntu on 2010-02-03
I would suggest putting that command in a script and running the script with full path via cron.  Make sure you capture the return status of rsync command in the script.  Also capture both stdout and stderr.

---

