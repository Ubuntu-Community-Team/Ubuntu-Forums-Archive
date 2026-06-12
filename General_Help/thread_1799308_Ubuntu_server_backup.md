---
title: "Ubuntu server backup"
date: 2011-07-07
forum: General Help
---

### Post by chkl on 2011-07-07
Any ideas how to backup a Ubuntu 11 server (to another hard drive) on a regular basis ? 
I want to get a backup of the entire partition every night (or at least every week), preferably without manual interference...
Also, the backup must be done without stopping the machine.
Anybody who knows of a tried and tested software solution ?

Thanks in advance !

---

### Post by collisionystm on 2011-07-07
> **chkl said:**
> Any ideas how to backup a Ubuntu 11 server (to another hard drive) on a regular basis ? 
I want to get a backup of the entire partition every night (or at least every week), preferably without manual interference...
Also, the backup must be done without stopping the machine.
Anybody who knows of a tried and tested software solution ?

Thanks in advance !

rsnapshot is your best tool.

Install it and add it to your crontab. If you need help configuring let me know

---

### Post by seawolf167 on 2011-07-07
Rsync + crontab

You can put the the $date in the filename and keep running backups with an optional script to remove files older than some date you set.

---

### Post by chkl on 2011-07-08
Thanks 'collsionystm', rsnapshot is installed and seems to work OK. There is one thing that I cannot figure out; what is the relation between the settings

#           BACKUP INTERVALS            #
interval    hourly    6
interval    daily    1
interval    weekly    4
#interval    monthly    3

in rsnapshot.conf and the settings in crontab:

00 01 * * * /usr/bin rsnapshot daily. I want one daily backup at 1 AM.

---

