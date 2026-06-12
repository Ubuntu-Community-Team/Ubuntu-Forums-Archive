---
title: "Permissions issue when making postgres backups in webmin"
date: 2012-04-29
forum: General Help
---

### Post by mcraul on 2012-04-29
HI,

I have an ubuntu server running 10.04.1 which I have webmin 1.52 installed. In the Postgres server tab in webmin you can setup and run backups of your databases. When I try to make a backup and choose the option "Create destination directory?" I choose Yes, because I want each backup in its own directory. When I click "backup now" the script fails and says permission denied when trying to write to the directory it just made and I have to log into the server and do a chmod to that directory and then run the backup in webmin again. So my question is why am I getting that permissions error when I try to make a directory in the postgres backup GUI? Shouldn't it make the directory its making automatically writable? or am I missing something? 

Hope I was clear enough, thanks!

---

### Post by SeijiSensei on 2012-04-29
The backups are probably being written by the "postgres" user, the username that the server runs as.  Using webmin to create those directories probably makes them owned by root and not writable by user postgres.

If I were you, I'd just write a little script that runs each night and dumps the database to a date-stamped file.  I use a script like this:

```

#!/bin/sh

LOG=/var/log/pgbackup.log
TODAY=$(date +%y%m%d)
STALE=$(date +%y%m%d --date='8 days ago')
BACKUP_DIR=/var/backups/db

mkdir -p $BACKUP_DIR
cd $BACKUP_DIR

echo -n "Postgres backup starting at " >> $LOG
echo $(date) >> $LOG

pg_dumpall -U postgres  > dump.$TODAY.sql 2>$LOG 
rm -f dump.$STALE.sql

echo -n "Postgres backup completed at " >> $LOG
echo $(date) >> $LOG


```

Using sudo, I put this script in a file called /usr/local/sbin/pgbackup with 744 permissions, then link to it from /etc/cron.daily like this:

```

sudo chmod 744 /usr/local/sbin/pgbackup
cd /etc/cron.daily
sudo ln -s /usr/local/sbin/pgbackup

```

Now the script will be run once each day at around 6:25 am.  The time is determined by the entry for cron.daily in /etc/crontab.  Each day's backup will be named dump.YYMMDD.sql and kept for eight days.

I don't give the postgres user a password. If you use a password, you need to add the "-w" option to the pg_dumpall command and create a /var/lib/postgresql/.pgpass file as described by reading "man pg_dumpall".

---

### Post by mcraul on 2012-05-02
Is there any way to get that postgres user the permissions to write to that directory that was just made?

Its just a little bit of a pain to make the directory in webmin then having to log into the server and chmod that directory then going back into webmin and running the backup. 


Thanks!

---

### Post by mcraul on 2012-05-02
Bump,  due to a spammer pushing down my post :(

---

