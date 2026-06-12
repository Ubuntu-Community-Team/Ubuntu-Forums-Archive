---
title: "backup script for ubuntu linux"
date: 2010-02-10
forum: General Help
---

### Post by computerguts on 2010-02-10
How would you create a script that backs up your hard drive to an external hard drive and a certian time every day?

---

### Post by K7522 on 2010-02-10
Do you want everything inside / or just certain folders? That will make a big difference in how the script is written.

---

### Post by cjhabs on 2010-02-10
Here is one that uses dump to back up your root partition - you must install dump.

#!/bin/sh

sudo dump 0nuf '/media/mounted_drive/Data/my_ubuntu_system_backup/root_'`date +%m%d%y`'.dump' /

simply create it in a text editor (cusotmize it to match your system mounts) and make it executable (sudo chmod +x scriptname) then add it to the scheduler using "sudo crontab -e"

---

### Post by t4thfavor on 2010-02-10
I posted a script not too long ago, I will repost it here, pretty self explanatory, but if you have questions, please feel free to ask.

Pretty much you put a space separated list of the folders you want backed up, and then schedule with cron to run it whenever you feel the need. It will backup to the location you specify.

make sure you run it as root, and maintain the older backups if you are low on space.

---

### Post by computerguts on 2010-02-11
everything on the hard drive needs to be backed up

---

### Post by cjhabs on 2010-02-11
Which partitions do you have configured? Each partition must be backed up separately.

---

### Post by Megafag on 2010-02-11
> **cjhabs said:**
> Which partitions do you have configured? Each partition must be backed up separately.

If they are mounted wouldnt they just back up via /media ?

EDIT: Divide by zero error.... it would keep backing up the backup.

---

### Post by computerguts on 2010-02-11
no, my hard drive does not automatically back up, is there backup software included in Ubuntu 9.04?

---

### Post by cjhabs on 2010-02-11
dump and restore are in the repositories
rsync is included
Either could do the job for you - I actually use dump to back up my root partition and rsync to backup my data partition - that's just for the hell of it - either works - and there are more options available.

---

### Post by t4thfavor on 2010-02-11
Remember you will have to have enough space to put all this backup on. If the entire drive needs to be backed up, just use rsync to sync to another folder/disk, and be done with it. The script I posted works best when you have a bunch of folders peppered around your system that need backing up, for archival purposes. That's why I gzip everything.

---

