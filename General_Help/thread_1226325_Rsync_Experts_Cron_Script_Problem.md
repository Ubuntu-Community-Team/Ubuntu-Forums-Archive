---
title: "Rsync Experts: Cron Script Problem"
date: 2009-07-29
forum: General Help
---

### Post by TheSpeedoBeast on 2009-07-29
The following script is my back up script. It starts out by determining what the previous backup directory's name is. Then hard links from that directory in my backup server to the new rsync folder, and copies the changed files to the backup server. When I run this script in terminal, it runs fine, but when I place this script in cron, it fails to run correctly; rsync runs, but the entire directory is copied over, instead of just the changed files. All of my directory references use direct links, so I'm not sure what the problem is. Any help here would be greatly appreciated. 

```
#!/bin/bash
ip="192.168.0.3"
day=`/bin/date +%Y%m%d`
time=`/bin/date +%H%M%S`
sudo chmod -R 777 /media/backup
lastline=`/bin/ls -l /media/backup | /usr/bin/awk '{print $8}' | /bin/grep 20 | /usr/bin/tail -1`

/usr/bin/rsync -av -e ssh --progress --exclude-from=/home/username/excludes --link-dest=/media/backup/"$lastline"/ root@"$ip":/media/sdc1/ /media/backup/"$day"_"$time"/
 
/usr/bin/rsync -av -e ssh --progress --exclude-from=/home/username/excludes --link-dest=/media/backup/"$lastline"/ root@"$ip":/media/sdb1/ /media/backup/"$day"_"$time"/

rm /media/backup/latest
ln -s /media/backup/"$day"_"$time" /media/backup/latest

```

---

### Post by TheSpeedoBeast on 2009-07-31
I hate to be the guy who keeps bumping posts over and over, but I wanted to give this one last try before I give up on this damn script : ) Thanks, everyone.

---

### Post by matey3 on 2009-07-31
> **TheSpeedoBeast said:**
> The following script is my back up script. It starts out by determining what the previous backup directory's name is. Then hard links from that directory in my backup server to the new rsync folder, and copies the changed files to the backup server. When I run this script in terminal, it runs fine, but when I place this script in cron, it fails to run correctly; rsync runs, but the entire directory is copied over, instead of just the changed files. All of my directory references use direct links, so I'm not sure what the problem is. Any help here would be greatly appreciated. 

```
#!/bin/bash
ip="192.168.0.3"
day=`/bin/date +%Y%m%d`
time=`/bin/date +%H%M%S`
sudo chmod -R 777 /media/backup
lastline=`/bin/ls -l /media/backup | /usr/bin/awk '{print $8}' | /bin/grep 20 | /usr/bin/tail -1`

/usr/bin/rsync -av -e ssh --progress --exclude-from=/home/shook/excludes --link-dest=/media/backup/"$lastline"/ root@"$ip":/media/sdc1/ /media/backup/"$day"_"$time"/
 
/usr/bin/rsync -av -e ssh --progress --exclude-from=/home/shook/excludes --link-dest=/media/backup/"$lastline"/ root@"$ip":/media/sdb1/ /media/backup/"$day"_"$time"/

rm /media/backup/latest
ln -s /media/backup/"$day"_"$time" /media/backup/latest

```


Hi I am no expert but I think if you declare your variables (i.e day , time etc) with CAPS it will be better because some of them may be already a command so they may execute interrupting your script.

I'll see what I can find...I post later.

---

### Post by DaithiF on 2009-07-31
Hi, if I had to guess I would say its a problem with your:
```
--link-dest=/media/backup/"$lastline"/
```

is your $lastline variable coming out as you expect?  (Add a line to echo $lastline > somefile so you can see what it produced after the fact)

The purpose of $lastline is to find the most recent directory on the backup partition, right?  
Couple of possibilities:
1. Couldn't you just simplify it to: 
```
ls -rt | tail -1
```
or
2. if you want to keep with the current approach, is the awk print **$8** correct?  I'm on cygwin-windows (@ work) at the moment so perhaps different for me, but ls -l | awk print $8 gives me a piece of the file timestamp.  For the filename I would need **$9**

again, echoing out $lastline from when cron runs may confirm.

good luck
D

---

### Post by matey3 on 2009-07-31
Sorry All I found were scripts dealing with backing up logical volumes, I have used FlyBack tho and it works good IF you have GUI installed bcs FlyBack program really doesnt have any non-GUI interface, it still works but you cannot see what it is doing meanwhile!
do a python flyback.py --backup and it will start to back up.(in the terminal)
(anyway google flyback to get more info, the gui I used seemed really cool but I dont think you can us it for remote servers :()

Anyway these are the scripts I found running on my server;
may be you can get an idea...
I have gone thru so many scripts last few days I have lost many of them (didnt book mark them), places like howtoforge have a lot of samples tho. 
like;
[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

Good Luck!

This is snapshot script using rsync;


#!/bin/bash

LV=$1

export PATH=$PATH:/sbin

echo Backing up $LV...
if ! [ -e $LV ]; then
  echo '  ...No such device exists!'
  exit 1
fi

NAME=`expr "$LV" : ".*\/\(.*\)$"`
NAME_SNAP=${NAME}_snap
LV_SNAP=${LV}_snap

/etc/init.d/udev restart
sleep 121
echo '  ...Creating snapshot'
lvcreate -s -n${NAME_SNAP} -L1024 $LV
RV=$?
while [ $RV -gt 0 ]
do
  lvremove -f ${LV_SNAP}
  sleep 121
  lvcreate -s -n${NAME_SNAP} -L1024 $LV
  RV=$?
done
mkdir -p /mnt/${NAME_SNAP}
echo '  ...Mounting snapshot'
mount ${LV_SNAP} /mnt/${NAME_SNAP}
echo '  ...rsyncing'
rsync -avz --delete -e "ssh" /mnt/${NAME_SNAP}/* 192.168.1.10:/mnt/${NAME}/
#cd /mnt/${NAME_SNAP}/
#echo '  ...Creating archive'
#tar czf /mnt/system_backups/${NAME}.tgz *
#cd /
echo '  ...Unmounting and removing snapshot'
umount /mnt/${NAME_SNAP}
lvremove -f ${LV_SNAP}
echo '  All done!'
echo
sleep 120
--------------------------

#!/bin/bash

DIR=/root/backup
BACKUP_CMD=backup-lv.sh ##The script above##

VG=/dev/vg1
LV[0]=v1
LV[1]=v2
LV[2]=v3
LV[3]=v4

cd $DIR
COUNT=0
CAT_STR=""
while [ $COUNT -lt ${#LV[@]} ]
do
  ./$BACKUP_CMD $VG/${LV[$COUNT]} &> last-backup-${LV[$COUNT]}
  CAT_STR="${CAT_STR} last-backup-${LV[$COUNT]}"
  MOO=$((COUNT++))
done

ls -lh /mnt/system_backups/ &> last-backup-ls
cat $CAT_STR last-backup-ls > last-backup.txt
echo "daily backup report attached" | mutt -s "$HOSTNAME daily backup report" -a last-backup.txt [email]my-email@domain.com[/email]

_______________________________________________

###this is backup-lv.sh file; Uses lv (logical volume) commands!

#!/bin/bash

LV=$1

export PATH=$PATH:/sbin

echo Backing up $LV...
if ! [ -e $LV ]; then
  echo '  ...No such device exists!'
  exit 1
fi

NAME=`expr "$LV" : ".*\/\(.*\)$"`
NAME_SNAP=${NAME}_snap
LV_SNAP=${LV}_snap

/etc/init.d/udev restart
sleep 120
echo '  ...Creating snapshot'
lvcreate -s -n${NAME_SNAP} -L1024 $LV
RV=$?
while [ $RV -gt 0 ]
do
  lvremove -f ${LV_SNAP}
  sleep 120
  lvcreate -s -n${NAME_SNAP} -L1024 $LV
  RV=$?
done
mkdir -p /mnt/${NAME_SNAP}
echo '  ...Mounting snapshot'
mount ${LV_SNAP} /mnt/${NAME_SNAP}
cd /mnt/${NAME_SNAP}/
echo '  ...Creating archive'
tar czf /mnt/system_backups/${NAME}.tgz *
cd /
echo '  ...Unmounting and removing snapshot'
umount /mnt/${NAME_SNAP}
lvremove -f ${LV_SNAP}
echo '  All done!'
echo
sleep 120

#The sleep is counted in seconds by default
-------------------------------------------------

---

### Post by TheSpeedoBeast on 2009-07-31
Thanks SO MUCH for your help everyone! I'm at work right now, so I can't test this fully, but it looks like cron might actually ls -l differently than running it in a simple shell prompt. When I ran that script in a terminal, it would echo back the filename correctly. However, when I ran the script in cron, it would echo back the timestamp (as DaithiF said). I will try those modifications when I get back home, but it is looking promising. Anyone know why the columns are different in cron than in a normal shell?

---

### Post by TheSpeedoBeast on 2009-07-31
Answered my own question... cron does ls -l differently than the standard shell:

drwxr-xr-x 2 username username 4096 2009-07-29 03:51 Videos
-rw-r--r-- 1 username username 357 Jul 29 08:40 examples.desktop

Dumb that it's not standard, but it is what it is. Hopefully this will help someone out.

---

### Post by unutbu on 2009-07-31
Thank you DaithiF, for pointing out this interesting cron pitfall.
I did a bit of experimenting and found the following:

If I put LANG=en_US.UTF-8 in my crontab, then "/bin/ls -l" behaves like 
it does in my terminal. So for you, you might want to type
```

echo $LANG
```

in the terminal, see what it returns, and then put
```

LANG=(whatever the terminal returned as the value of LANG)
```

at the top of your crontab.

When I ran
```

*    *	   * 	 *   *   /usr/bin/env > /tmp/env-without-lang.out
*    *	   * 	 *   *   /bin/ls -l /test > /tmp/ls-l-without-lang.out
```

in my crontab, I found cron does not set the LANG environment variable by default
and /bin/ls -l returns stuff like this:
```

-rw-r--r-- 1 user user   132 Jul 30 21:14 a
```

But when I put LANG=en_US.UTF-8 at the top of the crontab and run 
```

*    *	   * 	 *   *   /bin/ls -l /test > /tmp/ls-l-with-lang.out

```
I get 
```

-rw-r--r-- 1 user user   132 2009-07-30 21:14 a
```

(Note the difference in date format)

Edit: LOL, I've read this before. See [http://ubuntuforums.org/showpost.php?p=6943778&postcount=5](http://ubuntuforums.org/showpost.php?p=6943778&postcount=5)

---

