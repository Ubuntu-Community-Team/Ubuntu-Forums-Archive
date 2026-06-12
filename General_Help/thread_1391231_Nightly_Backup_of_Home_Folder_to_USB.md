---
title: "Nightly Backup of Home Folder to USB"
date: 2010-01-26
forum: General Help
---

### Post by tom.swartz07 on 2010-01-26
Hi all,

I have a really quick question-

I would like to set up some type of scheduled event to back up my entire /home folder to a USB drive.

I know about all of the various programs such as simple backup, etc. and have used them before. As far as I know, these programs cant do what Im trying to do.


Does anyone know what I could use to back up my files at a specific time to a specific USB device?



Preferably, I would like to just have a simple 
```
sudo cp /home /media/Cruzer
```
run every night at, say, 2am. 

The problem is- some files (such as symlinks and various files used by Google Chrome, etc) arent able to be copied while the OS is running. Thats fine by me- theyre only small things, like cookies and other crud. The copy command stops at each occurrence where it cant copy.

Any ideas?

---

### Post by llawwehttam on 2010-01-26
Why not use rsync?

---

### Post by t4thfavor on 2010-01-26
```

#!/bin/sh
####################################
#
# Backup to NFS mount script.
#
####################################
#use this portion to create mysqldumps in each users dir of their databases.


# What to backup. 
backup_files="/home /var/www/www.fultonit.net /etc /root"

# Where to backup to.
dest="/media/300-S/Backups/"

# Create archive filename.
day=$(date +%a)
time=$(date +%R)
hostname=$(hostname -s)
archive_file="$hostname-$day-$time.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files
#compress to save space.
#gzip -9 $dest/$archive_file
# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest


```
I have to rename the backup something without the ":" in it and without spaces to restore, but it helpe me to keep track of it. Try it out, I find it to work quite nicely.


Ignore the NFS part, that's just there for no reason. It will backup everything in the line

backup_files="/home /var/www/www.fultonit.net /etc /root"

to the location

dest="/media/300-S/Backups/"

Good luck

---

### Post by jamesisin on 2010-01-26
Great script.

Please mark your thread as SOLVED in Thread Tools above.

---

### Post by t4thfavor on 2010-01-26
I love me that script, It's far easier than most other solutions, and it's compressed by default :)

---

### Post by tom.swartz07 on 2010-01-26
> **t4thfavor said:**
> ...SCRIPT...
I have to rename the backup something without the ":" in it and without spaces to restore, but it helpe me to keep track of it. Try it out, I find it to work quite nicely.


Ignore the NFS part, that's just there for no reason. It will backup everything in the line

backup_files="/home /var/www/www.fultonit.net /etc /root"

to the location

dest="/media/300-S/Backups/"

Good luck

My question is- how can you edit it to delete the previous version of the backup?

Looking at the format of the script, it will run and continuously create new tar.gz files. Additionally, the script needs to be manually activated to run.

Could this be set up with cron? I have no idea how to use cron, so I wouldnt know for sure.

Dont get me wrong- I really appreciate the help! Its just that it doesnt fit what im trying to do- just yet.

---

### Post by jamesisin on 2010-01-26
How many of the old backups do you want to keep?  If you only want one backup (maybe not the best choice) you can simply change the naming convention and write the same file name each time.

---

### Post by t4thfavor on 2010-01-26
My cron is 0 0 * * * /home/chance/backup.sh

Since I only backup about 50 mb of stuff, I didn't need automatic cleanup. It could be added easily though.

```

#!/bin/sh
####################################
#
# Backup to NFS mount script.
#
####################################
#use this portion to create mysqldumps in each users dir of their databases.


# What to backup. 
backup_files="/home /var/www/www.fultonit.net /etc /root"

# Where to backup to.
dest="/media/300-S/Backups/"

#Number of Days to keep (larger is longer)
daysold=5

# Create archive filename.
day=$(date +%a)
time=$(date +%R)
hostname=$(hostname -s)
archive_file="$hostname-$day-$time.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files
#compress to save space.
#gzip -9 $dest/$archive_file
# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest;
echo "Cleaning files older than $daysold days old.";
for file in $(find ${dest} -name *.tgz -mtime +${daysold}); do
	echo "Deleting $file";
	rm -f $file;
done


```

---

### Post by tom.swartz07 on 2010-01-26
> **jamesisin said:**
> How many of the old backups do you want to keep?  If you only want one backup (maybe not the best choice) you can simply change the naming convention and write the same file name each time.

Id like to keep at least 2 previous versions, but no more. I definitely dont want to overwrite the current file there, as Id lose the entire file if the process fails halfway through. :eek:


How does one use cron? Perhaps I could edit the current script to fit my needs and run it with cron

---

### Post by t4thfavor on 2010-01-26
sudo crontab -e 

is how I do it, I guess there are folders now in ubuntu that get executed, but I never bothered to try them.

---

### Post by jamesisin on 2010-01-27
You can see a discussion between myself and another Ubuer at this thread concerning setting up a cron job for a backup script:

[http://ubuntuforums.org/showthread.php?t=1366759](http://ubuntuforums.org/showthread.php?t=1366759)

Should be very useful.

---

### Post by seanbw on 2010-03-21
I had a scare recently losing my documents folder so this script was a godsend as I am now using it. But I ran into two problems recently and I would appreciate some assistance. First there were some folders in my home that were not being backed up due to permission issues:
```
tar: /home/seanbw/Writer's Cafe Documents/Living With SSD (HTML)/Cover_Image2.png: Cannot open: Permission denied
tar: /home/seanbw/Writer's Cafe Documents/Living With SSD (HTML)/Cover_Image.png: Cannot open: Permission denied
```

second I tried to test the archive file by opening it with Archive Manager and after a long time, got an error message sayng missing EOF.

I would like to know how I can resolve the permissions iissues. The folders that are not beng backed up have only group and others access only permissons. Should I change that to access and write? I think that the permissions issue is causing the EOF error so if I sort that, EOF should go away.

Thanks for all the assist.

---

### Post by seanbw on 2010-03-21
Discovered that some were root and some were seanbw (me) but most had owner access and write only so I am not sure whether changing the root to me and allowng group access will mess the owning programs like calibre?
Is there a way to run this script as root whilst using cron?

---

### Post by phen0m on 2010-03-21
I'll admit to not reading the whole thread so take my advice with a grain of salt.

You probably want to change the owner of any files in your home directory to yourself rather than trying to run a backup script on your own files as root (generally you want to try to avoid running cron tasks as root). ```
sudo chown -R seanbw/: /home/seanbw
```

To run cron tasks as root, edit roots crontab file.  
```
sudo crontab -e
```

---

### Post by seanbw on 2010-03-23
[QUOTE=You probably want to change the owner of any files in your home directory to yourself rather than trying to run a backup script on your own files as root ```
sudo chown -R seanbw/: /home/seanbw
```To run cron tasks as root, edit roots crontab file.] [/QUOTE]
chown: invalid spec: `seanbw/:' was the error message. Any options to seanbw/: ?
Thanks

---

### Post by john newbuntu on 2010-03-23
That's a nice script by t4thfavor.  I use a similar one.  The one difference being I delete some of the crud in my home dir such caches in firefox, google, thumbnails, audio programs, trash etc prior to the backup.  Saves a good 30MB per backup in my case every day.

---

### Post by e24ohm on 2010-03-24
> **t4thfavor said:**
> ```

#!/bin/sh
####################################
#
# Backup to NFS mount script.
#
####################################
#use this portion to create mysqldumps in each users dir of their databases.


# What to backup. 
backup_files="/home /var/www/www.fultonit.net /etc /root"

# Where to backup to.
dest="/media/300-S/Backups/"

# Create archive filename.
day=$(date +%a)
time=$(date +%R)
hostname=$(hostname -s)
archive_file="$hostname-$day-$time.tgz"

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files
#compress to save space.
#gzip -9 $dest/$archive_file
# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest


```
I have to rename the backup something without the ":" in it and without spaces to restore, but it helpe me to keep track of it. Try it out, I find it to work quite nicely.


Ignore the NFS part, that's just there for no reason. It will backup everything in the line

backup_files="/home /var/www/www.fultonit.net /etc /root"

to the location

dest="/media/300-S/Backups/"

Good luck

That is one wicked script - Mate...you should put the GNU ELU in there, and take some super nice credit..

Very nice...thank you...Cheers!!!

---

