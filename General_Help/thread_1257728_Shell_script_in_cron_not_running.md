---
title: "Shell script in cron not running"
date: 2009-09-04
forum: General Help
---

### Post by parrimin on 2009-09-04
Hi,

I've made a script to backup some directories in my external hdd. In order to do it automatically every day, i did:
```
crontab -e
``` and put:
```
00 1 * * * /home/backupScripts/bckpScript
```
If I run my scrip manually, it makes backup successfully. But when run with cron, i see the result files are too much small. I mean, some result file has 2,5G in "manual mode", and 8,6M in "cron mode". So if the result files are made with cron, that means the script is running, but i cant understand why the result file is not the expected. Some ideas please?

The script code is:

```

#!/bin/sh
LOGFILE="bckpLogFile`date +%y%m%d`.log"
DISKPATH="/mnt/backupdisk"
day=$(date +%A)
BCKPPATH="$DISKPATH/$day"

startBCKP()
{
        mkdir $BCKPPATH
        echo ******************* `date`: Starting BACKUPS >> $BCKPPATH/$LOGFILE

        echo `date`: First Start backup >> $BCKPPATH/$LOGFILE
        tar -czvf $BCKPPATH/backupFirst.tgz /home/CVS
        echo `date`: First End backup OK >> $BCKPPATH/$LOGFILE

        echo `date`: Second Start backup >> $BCKPPATH/$LOGFILE
        find /home/ -maxdepth 2 -iname "backup" -type d -exec tar -czvf $BCKPPATH/backupSecond.tgz {} \;
        echo `date`: Second End backup OK >> $BCKPPATH/$LOGFILE

        echo `date`: Third Start backup >> $BCKPPATH/$LOGFILE
        tar -czvf $DISKPATH/backupRepos.tgz /home/repos --exclude /home/repos/Temp
        echo `date`: Third End backup OK >> $BCKPPATH/$LOGFILE
ISMOUNT=$(cat /proc/mounts | grep $DISKPATH)
if [ -z "${ISMOUNT}" ];
        then
                echo Not mounted
        else
                startBCKP
fi

```

---

### Post by dcstar on 2009-09-04
> **parrimin said:**
> 
........
If I run my scrip manually, it makes backup successfully. But when run with cron, i see the result files are too much small. I mean, some result file has 2,5G in "manual mode", and 8,6M in "cron mode". So if the result files are made with cron, that means the script is running, but i cant understand why the result file is not the expected. Some ideas please?
.......

Cron jobs run in their own environment, not the user environment - they are different.

---

### Post by parrimin on 2009-09-04
> **dcstar said:**
> Cron jobs run in their own environment, not the user environment - they are different.

So...

---

### Post by kjohri on 2009-09-04
It needs to be debugged. One way to proceed could be to run the cron job just after running it manually. You will get two sets of backups. Both these should be un-tarred to see whether all the files are there or not. It should throw some light on the problem. If you are running the cron job and the manual job at different times, the results would be different.

---

### Post by DaithiF on 2009-09-04
hi,
from a quick reading of the script, one line that strikes me as strange is this one:
```
find /home/ -maxdepth 2 -iname "backup" -type d -exec tar -czvf $BCKPPATH/backupSecond.tgz {} \;

```

so if you had directories like:
/home/tom/backup
/home/dick/backup
/home/harry/backup
I assume the intention is to tar them *all* up, but in fact -exec is going to run 3 times, each time creating a tar file containing only 1 of them.  so the end result will be a tar file containing whichever backup directory find found last.

maybe you want this instead:
```
find . -maxdepth 2 -type d -iname backup -print0 | xargs -0 tar czvf $BCKPPATH/backupSecond.tgz
```

---

