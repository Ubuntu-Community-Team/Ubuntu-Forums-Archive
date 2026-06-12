---
title: "Cron Doesn't run when in virtual terminal 1?"
date: 2011-03-22
forum: General Help
---

### Post by aflyingturtle on 2011-03-22
So I'm trying to run a backup script using cron. When I'm in the normal GUI interface (tty7) the backup script runs fine. But when I press ctrl-alt-F1 and leave the computer in the first virtual terminal (tty1) The cron backup doesn't work. Doesn't do anything. Also, I'm running it from sudo's crontab.

The shell script is
```
 #!/bin/sh
####################################
#
# Backup to NFS mount script.
#
####################################

# What to backup. 
backup_files="/etc/mc/world"

# Where to backup to.
dest="/home/jacob/backups"

# Create archive filename.
day=$(date +[%H]%m~%d~%y)
hostname=$(hostname -s)
archive_file="save$day.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files

# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest 
```

Crontab:

@hourly /etc/mc/backup.sh

---

### Post by DaithiF on 2011-03-23
I don't suppose you have an encrypted home directory?

if so the directory would only be decrypted and readable by root when your user is logged in.  I don't know if theres a distinction between being logged in to a graphical desktop session vs. a virtual terminal for this purpose, but maybe.

---

