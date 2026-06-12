---
title: "Can't seem to get this cron job to work"
date: 2011-04-12
forum: General Help
---

### Post by CrazeDIzzleD on 2011-04-12
So I have a bash backup script that I want to run every day at 6:00AM. I set a cron job but it doesn't appear to be running, as no backup is created. If I run the script manually it works without any issues.

Here is my script:
```
#!/bin/bash

_WWW=www.tar.bz2
_MYSQL=mysql.tar.bz2
_DIR=$(date +%m-%d-%Y)
_WWWTARGETPATH=/var/www
_MYSQLTARGETPATH=/var/lib/mysql
_DESTPATH=/home/scott/backup/_BACKUP/$_DIR

mkdir /home/scott/backup/_BACKUP/$_DIR

cd $_WWWTARGETPATH
tar vfcpj $_WWW $_WWWTARGETPATH 2>> /var/log/backup.txt

mv $_WWW $_DESTPATH/$_WWW

/etc/init.d/mysql stop

cd $_MYSQLTARGETPATH
tar vfcpj $_MYSQL $_MYSQLTARGETPATH 2>> /var/log/backup.txt

mv $_MYSQL $_DESTPATH/$_MYSQL

/etc/init.d/mysql start
```

And my crontab
```
0 6 * * * /bin/backup.sc
```

My only thought is that my script requires root to run, so maybe cron doesn't have the right permissions.

Thanks.

---

### Post by DaithiF on 2011-04-13
Hi, a few things:
1. if it needs to run as root then put it in root's crontab rather than your own.  Your own crontab runs command as you.
There are a variety of root-level crons where you could put it, one of which is to do:

```
sudo crontab -e
```

2. You're likely running into the error described in my post in this thread: [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242)

Use the solution there (put 
MAILTO=''
at the top of the crontab (ie. before the commands to be run).

3. Its good practice to log the output of your cron jobs so that you can see whats happening when errors occur.
Append** > /path/to/some/logfile 2>&1** to the end of your command to capture stdout and stderr output to a file.

---

### Post by falko on 2011-04-13
Try to define a PATH avariable at the top of your script, OR use full paths to your commands in your script (e.g. /bin/cp instead of just cp - the same goes for mkdir, tar, mv).

---

### Post by CrazeDIzzleD on 2011-04-14
> **DaithiF said:**
> Hi, a few things:
1. if it needs to run as root then put it in root's crontab rather than your own.  Your own crontab runs command as you.
There are a variety of root-level crons where you could put it, one of which is to do:

```
sudo crontab -e
```

2. You're likely running into the error described in my post in this thread: [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242)

Use the solution there (put 
MAILTO=''
at the top of the crontab (ie. before the commands to be run).

3. Its good practice to log the output of your cron jobs so that you can see whats happening when errors occur.
Append** > /path/to/some/logfile 2>&1** to the end of your command to capture stdout and stderr output to a file.

I did all of these things and now it works. Thanks!

---

