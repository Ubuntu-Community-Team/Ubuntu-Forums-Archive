---
title: "Backup mysql data from one server to another using rsync and ssh not working"
date: 2009-07-21
forum: General Help
---

### Post by rekha_shp on 2009-07-21
Hi

I want to create a cron job to run backup file automatically using rsync.I read the following link and used to make a passwordless rsync command.But it is asking for a password.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html) 

Pls help me.

---

### Post by rekha_shp on 2009-07-24
Hi

Anyone pls give me a solution.

---

### Post by trwww on 2009-07-24
Can you ssh to the machine with a basic ssh client?

Google 'paswordless ssh' and that should get you going.

---

### Post by NoReflex on 2009-07-24
Hello!

Are you sure simply copying mysql data files would give you a consistent snapshot of the database? I'm not sure about his one but I tend to believe it's not a safe procedure.
Are you using MyISAM or InnoDB?
I use MySQL with replication and I do all the backups with mysqldump. You won't need ssh. You can make a cron job and it won't require a password.
Here's a simple backup script:
```
#!/bin/bash
### Dump database and archive it ###
MYSQL_USER="your_user" 
MYSQL_PASS="your_password"
MYSQL_HOST="your_host" #192.168.1.5 for example
MYSQL_DB="your_database" # the database you want to backup
FILENAME="/var/backup/backup_"$(date +"%d-%m-%Y")
echo "Starting at: " $(date +"%d-%m-%Y %H:%M:%S")
mysqldump -u $MYSQL_USER -p$MYSQL_PASS -h $MYSQL_HOST $MYSQL_DB > $FILENAME.sql
echo "Dump completed at: " $(date +"%d-%m-%Y %H:%M:%S")
7z a -t7z -parchive_password -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on $FILENAME.7z $FILENAME.sql
echo "Archive completed at: " $(date +"%d-%m-%Y %H:%M:%S")
rm $FILENAME.sql
echo "SQL Dumps deleted. END"

```This will dump the database of your choice and will archive it to save space.
A cron job for this would look like:
```
# m h  dom mon dow   command
15 02 * * * /home/username/dump.sh > /var/backup/backup_log
```
I hope this helps you!

PS: I'm using MySQL at work for now because that's how it has been done around here but I strongly recommend PostgreSQL over MySQL (I'm in the process of migrating). Note that MySQL has been bought by Sun which in return has been bought by Oracle so MySQL's future is uncertain if you ask me. PostgreSQL isn't owned by anyone and has a BSD license. There are also performance, security and safety benefits in using PostgreSQL.
All I'm saying is if you have a bigger (or important) project PostgreSQL is the way to go. Just my 0.02 $

Best wishes,
NoReflex

---

