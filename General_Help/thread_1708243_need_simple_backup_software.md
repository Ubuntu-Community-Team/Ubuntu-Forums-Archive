---
title: "need simple backup software"
date: 2011-03-16
forum: General Help
---

### Post by CrazeDIzzleD on 2011-03-16
So I have a ubuntu web server, and I would like to backup two complete directories, to two different destinations.

This is what I require:
-Must support multiple destinations
-Must preserve directory/file permissions and structure
-Must be able to backup to a folder that is timestamped (IE: if doing a weekly backup, the backedup structure would look like: /backup/1-1-11, 1-8-11, 1-15-11 ... )

Also, being able to compress the backups would be a very nice bonus.

Does anyone know of software that meets my needs, or will I have to write something?

---

### Post by seawolf167 on 2011-03-16
You can take a look at sbackup, but I think you'll want to write your own script to backup your computer

sbackup

```
sudo apt-get install sbackup
```custom script using rsync and cron

```
gedit backup-script.sh
```then include the contents, something like this to mirror the files (obviously modified with your source/destinations/options

```

#!/bin/bash

rsync -ruv --delete  /source /destination1
rsync -ruv --delete  /source /destination2

```or like this to tar the files then compress the tarballs

```

#!/bin/bash

tar -cvf /path/to/destination/backup-file-name.tar.bz2 /path/to/backup/source

```make the script executable

```
sudo chmod +x backup-script.sh
```then add a line in crontab to run the script automatically

```
gksudo gedit /etc/crontab
```add a line like

```
00 0 * * * root /path/to/your/script/backup-script.sh
```EDIT: Forgot you wanted the date/time in your filename, just change or append the filename with something like this

```
filename-$(date +%m-%d-%y).tar.bz2
```

---

### Post by r.osmanov on 2011-03-16
Also consider using **logrotate**. In some cases very effective, flexible and handy backup tool.

---

### Post by ant2ne on 2011-03-16
Here is a simple backup script.
```
nano /bin/bkup.sc
```
paste the following
```

#!/bin/bash
_TARGETPATH=/data/to/be/backedup
_DESTPATH=/backup/destination
_MYFILE=$(date +%a)_yourbackupsname.tar.bz2

du -h --max-depth=1 $_TARGETPATH >> /tmp/backup/log.txt
cd $_TARGETPATH
tar vfcpj $_MYFILE $_TARGETPATH 2>> /tmp/backup/errorlog.txt
mv $_MYFILE $_DESTPATH/$_MYFILE

```Then execute it with cron

---

### Post by CrazeDIzzleD on 2011-03-16
Thanks for the bash scripts, that should work fine.

---

### Post by ant2ne on 2011-03-17
you could probably omit the du line. It just tells you the size of the data before backing it up and compressing it. I used it just for comparison.

---

