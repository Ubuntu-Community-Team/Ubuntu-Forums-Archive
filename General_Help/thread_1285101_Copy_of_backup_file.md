---
title: "Copy of backup file"
date: 2009-10-07
forum: General Help
---

### Post by mfoster1012 on 2009-10-07
I am new to the wonderful world of Linux and have a quick question that i have not been able to find an answer to.  I have already set my system to backup using sbackup but was wondering if there was a way to either automatically copy that backup file to a second location or to set it to back up to two locations so i will always have 2 copies of the backup file?  Thanks in advance.

---

### Post by mfoster1012 on 2009-10-12
Anyone at all?

---

### Post by mfoster1012 on 2009-10-15
Would the only way to do this be to manually copy to the second backup hard drive?

---

### Post by Zill on 2009-10-15
I suggest you write a shell script, save it as root, make it executable then setup a root crontab run the script as a cron job.  An example of such a script (myscript.sh) is shown below:
```
#!/bin/bash
#
#*path*/myscript.sh
# Script to copy latest backup file from *path*/location1 to *path*/location2
# To be run daily by root (sudo) crontab:
# 	crontab edit	=	crontab -e
# 	crontab list	=	crontab -l
# 	crontab remove	=	crontab -r
#
# crontabs are located in /var/spool/cron/crontabs
#
# m h  dom mon dow   command
# 15 5 * * * *path*/myscript.sh
#
cd *path*/location1
cp -r `ls --sort=time|head -1` *path*/location2
```
The script will copy the latest backup file in directory location1 to directory location2.  My crontab runs the script at 0515 every day - you should change this (with sudo crontab -e) to suit your requirements.  You will also, of course, need to use the correct paths to your files in the script!

See the following man entries for more information:
```
man cp
man crontab
```

---

