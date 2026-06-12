---
title: "Using tar to back up a QNAP server"
date: 2011-11-21
forum: General Help
---

### Post by mackconsult on 2011-11-21
I have the following script that have developed for my QNAP TS259.  Planning on having it run automatically using crontab.

backup.sh:

#!/bin/sh
####################################
#
# Backup to eSATA on NAS TS259.
#
####################################

# What to backup. 
backup_files="/share/music/ /share/Web/ /share/video/ /share/sheri.mccormack/ /share/Download/ /share/pictures/ /share/Data/"

# Where to backup to.
dest="/share/eSATADisk1/"

# Create archive filename.
day=$(date +%A)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"

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

When I run it there is a tar file created on my external eSATA drive but it is only 160 bytes and runs very quickly.  I don't think it is including the files and sub directories.  Is there something I am missing?

---

