---
title: "Shell script not working in cron"
date: 2010-01-20
forum: General Help
---

### Post by malikp on 2010-01-20
Hello,
I'm creating a script all worked fine in the command line. But not work in the cron. Below you could see the script

#!/bin/sh
LOGFILE=/home/transfield/mou/test.log
# Find yesterday Date and copy files
TODAY=$(date --date= +%F)
YESTERDAY=$(date --date="1 day ago" +%F)
YESTERDAY1=$(date --date="2 day ago" +%F)
echo $TODAY >> $LOGFILE
echo $YESTERDAY >> $LOGFILE
echo "## Copying processed files ##" >> $LOGFILE
ls -l /var/lct/mou2/processed | grep $TODAY | awk '{print " " $8}' > /home/trans/mou/processedfiles
ls -l /var/lct/mou2/processed | grep $YESTERDAY | awk '{print " " $8}' >> /home/trans/mou/processedfiles
exit


So far I found when I use corn following part not working, nothing goes to the processedfiles file.
ls -l /var/lct/mou2/processed | grep $TODAY | awk '{print " " $8}' > /home/trans/mou/processedfiles
ls -l /var/lct/mou2/processed | grep $YESTERDAY | awk '{print " " $8}' >> /home/trans/mou/processedfiles

This work perfect in command line. Corn job and command line use by the same user.
Hope some one could direct me to correct path.

thank you,

---

### Post by Barriehie on 2010-01-21
What does your syslog show when the job is called???

---

### Post by JohnFH on 2010-01-21
You have the logfile specified in the transfield user, but the processed files in the trans user.  The paths are different - is that what you want?

Does the directory /home/trans/mou exist?

Can you confirm that the first part of the script is being run by cron correctly?

---

### Post by malikp on 2010-01-21
Barriehie,> What does your syslog show when the job is called???
syslog show only script executed.
This is the part of the syslog
Jan 22 09:00:01 sysdb CRON[24999]: (malik) CMD (sh /home/malik/test/Tmoustart)
Jan 22 09:00:56 sysdb crontab[25030]: (malik) BEGIN EDIT (malik)
Jan 22 09:01:01 sysdb crontab[25030]: (malik) REPLACE (malik)
Jan 22 09:01:01 sysdb crontab[25030]: (malik) END EDIT (malik)
Jan 22 09:01:18 sysdb crontab[25036]: (malik) LIST (malik)
Jan 22 09:02:01 sysdb cron[880]: (malik) RELOAD (crontabs/malik)
Jan 22 09:02:01 sysdb CRON[25040]: (malik) CMD (sh /home/malik/test/Tmoustart)

JohnFH,
> Can you confirm that the first part of the script is being run by cron correctly?
Yes those path exist. Any way now I move everything to my own home folder to simplify everything

I'm using Ubuntu 9.10 server 64 bit.
so far I try following cron lines and syslog show script executed but nothing goes to the processedfiles
49 08 * * * /home/malik/test/Tmoustart
02 09 * * * sh /home/malik/test/Tmoustar

This is my modified script.
```
#!/bin/bash
. $HOME/.profile
LOGFILE=/home/malik/test/test.log
# Find yesterday Date and copy files
TODAY=$(date --date= +%F)
YESTERDAY=$(date --date="1 day ago" +%F)
YESTERDAY1=$(date --date="2 day ago" +%F)

echo $TODAY >> $LOGFILE
echo $YESTERDAY >> $LOGFILE
echo $YESTERDAY1 >> $LOGFILE
echo "## Copying prossed files ##" >> $LOGFILE
ls -l /var/lct/mou2/processed | grep $TODAY | awk '{print " " $8}' > /home/malik/test/processedfiles
ls -l /var/lct/mou2/processed | grep $YESTERDAY | awk '{print " " $8}' >> /home/malik/test/processedfiles
exit
```



Still I can see when I run on the terminal worked fine. But in  the cron following part with ls not working.
```
ls -l /var/lct/mou2/processed | grep $TODAY | awk '{print " " $8}' > /home/malik/test/processedfiles
ls -l /var/lct/mou2/processed | grep $YESTERDAY | awk '{print " " $8}' >> /home/malik/test/processedfiles
```
I add  . $HOME/.profile to pick-up the environment variables. Hope that's the correct way.

---

### Post by malikp on 2010-01-21
Hello all I mange to fix the problem using find command. But still I do not know why grep failed. I found grep failed with any number. if I use characters work fine.

Basically I used the script to find last 3 days  files in a folder and copy to another location.
using find command as below I mange to do the same and also that make my script smaller too
find /var/lct/mou2/processed/ -mtime -2 > /home/trans/mou/processedfiles
```
#!/bin/bash
LOGFILE=/home/malik/test/test.log
find /var/lct/mou2/processed/ -mtime -2 > /home/trans/mou/processedfiles
exit 
```
Now all worked fine with cron and command line. using the content of the processedfiles I can copy the files.

Thanks you for helping me

---

### Post by john newbuntu on 2010-01-21
I just found that you solved it .  Ignore this.

---

### Post by Barriehie on 2010-01-22
Find is a cool command!  Even though solved try your grep command like this **${whatever}** and see if that makes a diff.

---

