---
title: "Cronjob not starting my backupscript"
date: 2011-04-18
forum: General Help
---

### Post by schlupo on 2011-04-18
HI,

I wrote a little backupscript wich is working fine if i start it from the shell manualy.
But I'm not able to let it start automaticaly via cron in ubuntu 10.10.
Can you please help me out with this one ?

Here the bashscript:


[I]#!/bin/sh
####################################
#
#
#
####################################

# Which folder to backup
backup_files="/var/www/rspwiki"

# Where to backup to.
dest="/home/olivier/backup"

# Create archive filename for rspwiki folder.
day=$(date +%A)
archive_file="rspwiki-folder-$day.tgz"

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files

#Craeting compressed MySQL dump
mysqldump -h localhost -u wikiuser -1234 wikidb | gzip > /home/olivier/backup/MySQL-dump-$day.sql.gz

---------------------------------------------------------------

[/I]I typed sudo crontab -e[I]
and added the following line to start the script at 10 pm:

0 22 * * * bash /home/olivier/backup.sh

----------------------------------------------------------------
[/I]
I'm a total noob...never used cron before.....thanks for help

Peace

---

### Post by thecamelcoder on 2011-04-18
Hey mate, 

Right, well you don't need to use sudo if you are editing your own crontab. crontab is user specific nad yours is different than every other users. by typing sudo before had all you are doing is impersonating root.

Best option is just do a normal crontab -e. Paste in your records as you have listed them above. 

You want to try and capture the output when the job runs so you can debug the issue a bit further. 

if you have sendmail installed crontab will automatically send the output of the job to user@localhost and should be visible by entering `mail`.

Failing that you can set MAILTO="user@domain.com" on the first line of my crontab, this will send the output to your email address if you have a MTA or mail transfer agent installed, like sendmail. 

If you looking for more linux howto's and linux tutorials have a look at [http://www.linux-geek.co.nz](http://www.linux-geek.co.nz)

):P

---

