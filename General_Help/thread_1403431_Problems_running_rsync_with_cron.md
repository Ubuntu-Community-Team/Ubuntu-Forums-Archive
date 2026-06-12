---
title: "Problems running rsync with cron"
date: 2010-02-10
forum: General Help
---

### Post by Trader2699 on 2010-02-10
Hello all, my apologies if this is posted in the wrong place. First time poster here, and a Linux newbie. 

I have a box running Ubuntu 9.04, and I am using rsync within a script to backup files to a remote directory. 

In the /etc/fstab I have: 

*All variables notated being in (parenthesis). 

//(IP ADDRESS)/(SHARE NAME) /mnt/backup cifs username=(domain)\(username),password=(password)

Then I have a script in /root called runbackup.sh which is:

#!/bin/bash
PATH=/bin:/usr/bin
mount /mnt/backup
/bin/echo `date +\%Y.\%m.\%d` > /etc/last_backup.txt
/usr/bin/rsync -avz /etc /mnt/backup/aidclxcicada
/usr/bin/rsync -avz /home /mnt/backup/aidclxcicada
/usr/bin/rsync -avz /opt/Cicada/apache2 /mnt/backup/aidclxcicada
umount /mnt/backup
exit 0

The idea being that when the script runs, it mounts the remote directory, runs the backup, then dismounts. I can run the script fine from the command line as:

sh runbackup.sh

and everything goes through. You can see that there is a textfile marking the date when the backup last ran so I can easily check. 

The problem comes when I want to automate the job. In my crontab I have:

50 2    * * *   root    nice -n 19 /root/runbackup.sh &> /root/backuplogs/`date +\%Y.\%m.\%d`.log

So, it should run at 2:50 AM every morning and create a log with that date in /root/backuplogs. The problem is that it is creating a log file, but it's not populated, it's just a blank file. Also, it's not creating the new textfile in /etc/, leaving me to think it's hanging up somewhere and not running. 

Any clues?

---

