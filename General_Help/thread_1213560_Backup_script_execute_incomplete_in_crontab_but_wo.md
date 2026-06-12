---
title: "Backup script execute incomplete in crontab but working by manual"
date: 2009-07-14
forum: General Help
---

### Post by enzo_ong on 2009-07-14
Hi all,

I'm new to Ubuntu. I had write a shell script that archive files in a directory that the last modify date more than 7 days into another archive directory and then remove the original file. when i manually execute the script it run completely without error, but i will only run half way if execute through crontab.

I'm running ubuntu 4.2.4


The following is my shell script:

#!/bin/sh

START="/var/source"
dest="/var/archive"
LOGFILE="/var/archive/archive.log"
day=$(date +%Y%m%d)
FILE_AGE_Sec=604800    #5184000        #7776000
DAY_COUNT=7   #Optional: for display or "echo" purpose only.
archive_file="$hostname-$day.bz2"
FILES="*"
EXCLUDE_DIR="campaigns"
CURRTIME=$(date +%s)

if [ ! -f $LOGFILE ]
then
        touch $LOGFILE


fi

echo "$-----------------------------------------------" >> $LOGFILE

if [ ! -d $START ]
then
        echo "$(date) START Directory not found!" >> $LOGFILE
        echo "$(date) Archive Fail and Exit!" >> $LOGFILE
        echo "$START not a directory!"
        exit 1
fi

# use find command to get all subdirs name in DIRS variable
DIRS=$(find "$START" -type d)

# loop thought each dir to get the number of files in each of subdir

echo "Backup Begin........................"
echo "$(date) Archive Begin...." >> $LOGFILE
for d in $DIRS
do
   [ "$d" != "." -a "$d" != ".." ] &&  echo "$d dirctory has $(ls -l $d | wc -l) files" || :

   if [ $(echo $d | grep "campaigns") ]
   then

   echo "Founded: Skip! : $d" >> $LOGFILE

   else
   for i in $d/$FILES
   do


   if [ -f $i ]
   then
   MOD_DATE=$(date +%s -r $i)
   FILE_AGE=$(($CURRTIME-$MOD_DATE))
   ACT_AGE=$(($FILE_AGE/86400))

   [ -f $i ] && echo "$i Last Modification : $FILE_AGE"


     if [ $FILE_AGE -gt $FILE_AGE_Sec ]
     then
        BASE_EXT=${i##*.}
        if [ $BASE_EXT != "sq3" ] && [ $BASE_EXT != "db" ]; then

        echo "This file more than $DAY_COUNT days old!"

        BNAME=$(basename $i)
        BNAME_DIR=$(basename $d)
        ARC_Path="$dest/$BNAME_DIR"
        ARC_Path_Name="$ARC_Path/$BNAME.$day.bz2"
        if [ ! -d $ARC_Path ]
        then

        mkdir $ARC_Path

        echo "New Directory Created: $ARC_Path"

        fi
        tar cjPf $ARC_Path_Name $i
        #echo "$i" >> /var/maintenance_adstat/archive/achive45.list
        echo "Archieve: $ARC_Path_Name  Done!"

        rm $i            #Remove the original file.

         fi
     fi

   fi
   done
   echo
   fi
done

echo
echo "Backup finished!"
echo "$(date) Backup Finished!!!" >> $LOGFILE
echo "$-----------------------------------------------" >> $LOGFILE



My crontab:
30 3 * * * /var/archive/archive.sh


That's something wrong in my shell script or cron environment? I hope anyone can help to give me some solution or idea.

Thanks and Regards,

Enzo

---

### Post by Slim Odds on 2009-07-14
Yes, the environment is very difference between cron and your usr account.

You generally need to use full paths for executables, etc.

---

### Post by enzo_ong on 2009-07-15
> **Slim Odds said:**
> Yes, the environment is very difference between cron and your usr account.

You generally need to use full paths for executables, etc.

My script is using full path.

Difference between con and my usr account? can u explain further.

Sorry i new to ubuntu. Thanks

---

### Post by fridaythe14th on 2009-07-15
When a script/command is run with cron all the variables you normally have set are not set. You can define variables in your crontab file (the one that opens when you write "crontab -e"). Just write them at the top over the actual jobs, like this:

```

#variables
BASH=/bin/bash
HOME=/home/me
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

#jobs
@daily /home/me/scripts/backup

```

With the command "set" you get a list of defined variables.

You could just output set to a file "set > file.txt", open it and copy paste to the top of your crontab file. That's sort of what I did to solve this and it worked, but there's a lot of junk in there like functions, and I'm not sure how cron would react if you would paste those. There are also some other variables like PWD that is sort of useless to define there.

---

### Post by Slim Odds on 2009-07-15
> **enzo_ong said:**
> My script is using full path.

Difference between con and my usr account? can u explain further.

Sorry i new to ubuntu. Thanks

You're not using full paths to executable files like find and date. Even the path is different between cron and usr account.

---

### Post by enzo_ong on 2009-07-16
> **fridaythe14th said:**
> When a script/command is run with cron all the variables you normally have set are not set. You can define variables in your crontab file (the one that opens when you write "crontab -e"). Just write them at the top over the actual jobs, like this:

```

#variables
BASH=/bin/bash
HOME=/home/me
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

#jobs
@daily /home/me/scripts/backup

```With the command "set" you get a list of defined variables.

You could just output set to a file "set > file.txt", open it and copy paste to the top of your crontab file. That's sort of what I did to solve this and it worked, but there's a lot of junk in there like functions, and I'm not sure how cron would react if you would paste those. There are also some other variables like PWD that is sort of useless to define there.

I did copy and paste those code in my script. i cp the scrip to my user directory. and i change the cron job path as u mentioned. but it still not working... 

Can any body help? Thanks

---

### Post by enzo_ong on 2009-07-16
> **Slim Odds said:**
> You're not using full paths to executable files like find and date. Even the path is different between cron and usr account.

Hi,

i had copy the exactly same script and run in another machine... it work perfectly fine in cron. For this machine, it also consist of other cron job that doing rsync stuff... all those rsync work well just my backup script. so wat the problem actually?

I hope you can help me. Thanks

---

### Post by enzo_ong on 2009-07-19
somebody help~~

---

