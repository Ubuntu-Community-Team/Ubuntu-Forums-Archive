---
title: "Help creating shell script from source code for cron"
date: 2010-01-31
forum: General Help
---

### Post by neilevan814 on 2010-01-31
This is regarding the KDE application Basket:

I want to create a shell script that I can run as a cron job to do automated backups.  I have no idea how to proceed.  I have the source code and have pulled out the backup source files. Here is the link for the source code.  The download is at the bottom of this page.  The backup files can be found in the src folder listed as backup.cpp and backup.h
[SIZE=2][COLOR=Blue][http://www.kde-apps.org/content/show.php/BasKet+Note+Pads?content=10020](http://www.kde-apps.org/content/show.php/BasKet+Note+Pads?content=10020)[/COLOR][/SIZE]

If someone can do this, I believe it will make a nice addition to the Basket application for all.

Also I am not running Kubuntu I am running Karmic 9.10 64 bit

---

### Post by t4thfavor on 2010-01-31
I have a backup script.

```

#!/bin/sh
####################################
#
# Backup to somewhere script.
# Launch this with 3 args
# Backup Files in the form of "/dir/subdir /dir /home/user" What to backup
# Backup Location In the form of "/media/drive/Backups" Where to put it.
# Backup Prefix in the form of "customBackupFileName" What to prefix the backup files with.
# Or launch it without any args, and get the options specified in the script section under startup.
####################################
#use this portion to create mysqldumps in each users dir of their databases.




####################################
#
#Arg Processing, and setup.
#
####################################
EXPECTED_ARGS=3

#Create archive filename.
day=$(date +%a)
time=$(date +%R)
hostname=$(hostname -s)

#Days to keep (larger is longer)
daysold=15
#If I get 3 args, Use them.
if [ $# -ne $EXPECTED_ARGS ]
then
  #This is what happens when you just run the script no args.
  echo "No Custom Args specified, standard Args being used"
  echo "Backing up standard locations";
  #What to backup
  backup_files="/home /var/sites /etc /root";
  #Where to back it up to.
  dest="/media/300-S/Backups";
  archive_file="$hostname-$day-$time.tgz"
else
  #This is what happens when you launch it with correct args.
  echo "Backing up custom locations";
  # What to backup.
  backup_files=$1;
  # Where to backup to.
  dest=$2
  #prefix the filename
  archive_file="$3_$hostname-$day-$time.tgz"
  
fi  
###########################
#
#Main Script
#
###########################

# Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo

# Backup the files using tar.
tar czf $dest/$archive_file $backup_files

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

If you can't understand what it's doing, let me know, and I will attempt to explain  it.

---

### Post by neilevan814 on 2010-02-01
Hello t4thflavor,

I have a similiar backup script I use for directories and full backups, but what I am asking is for a specific backup of an application.  You know, like Evolution mail client...you can backup and restore as one of their file options??  I found a guy who actually made a cron useable shell script for backing up Evolution automatically and that works great.  These applications are a little tricky and require script lines only designated in their source codes.  I do not know nearly enough about programming to decipher the source for this Basket program.  If you have any ideas for that....Many many thanks.

---

### Post by t4thfavor on 2010-02-01
What are the specific things you would like to backup? I will probably be able to help formulate a script to accomplish some automated app backups.

What that backup.cpp/h appears to do is just backup the basket application. I don't think that the basket project has any interest in backing up other applications, as that doesn't look like their focus.

---

### Post by neilevan814 on 2010-02-01
t4th,

I think you misunderstand me.  I just want to automate the backup of my Basket program.  Simply applying a tar command to the .baskets folder where the files for basket backups are located does not yeild a valid backup.bz2 or .gz

---

### Post by t4thfavor on 2010-02-01
I still think you could manually backup the folder with tar -czf archive.tgz basket/folder , and then restore it manually, and it would probably work fine. But for the sake of being complete.

Looks like the program creates a tar file with a special name thats documented here

/**
 * Backups are wrapped in a .tar.gz, inside that folder name.
 * An archive is not a backup or is corrupted if data are not in that folder!
 */
const QString backupMagicFolder = "BasKet-Note-Pads_Backup";

So if you ran this command

tar -cvf /path/to/BasKet-Note-Pads_Backup/backupname.tar.gz /folder/to/backup/

you should get a file worthy of being restored by basket.

I do not run KDE, so you will have to test, and get back with me.

---

### Post by neilevan814 on 2010-02-01
t4th,

Thanks.  This is the farthest I've gotten.  However, I can't find a path to Basket_Note_pads_Backup .  There must be a call to the backup.cpp that would initiate a string of actions.  I don't know enough programming to figure this out.  The Evolution backup.c file had a void function that was the heart of the backup procedure.  The guy..and I wish I knew his name off the bat...but, that figured that out extracted the shell script instructions to make a bash shell script.  Here is what he came up with from that void funtion

#!/bin/bash
USERNAME=shane
BACKUP_FILE="/home/${USERNAME}/Ubuntu One/evolution-backup.tar.gz"
if [ -f "${BACKUP_FILE}" ]
then
rm "${BACKUP_FILE}"
fi
evolution --force-shutdown
rm /home/${USERNAME}/.evolution/.running
gconftool-2 --dump /apps/evolution > /home/$USERNAME/.evolution/backup-restore-gconf.xml
cd /home/${USERNAME} && tar czhf "${BACKUP_FILE}" .evolution `if [ -d .camel_certs ]; then echo .camel_certs; fi`
evolution &
disown

There is no nice little extractable function that I can find that resembles the commands given here.  

It may just not be able to be done.  I don't know.  But either because I am lazy or forgetful.  I would like a script like that with which I can set a daily cronjob calling it.

---

### Post by t4thfavor on 2010-02-01
It doesn't look like the dev's english is pristine, maybe I misunderstood in usage. Perhaps the backupMagicFolder has to be inside the tar in order for it to be restored.

Take a look inside a real backup, and tell me if you see something resembling it.

Indicated by the restore routine.
```

void RestoreThread::run()
{
	m_success = false;
	KTar tar(m_tarFile, "application/x-gzip");
	tar.open(IO_ReadOnly);
	if (tar.isOpened()) {
		const KArchiveDirectory *directory = tar.directory();
		if (directory->entries().contains(backupMagicFolder)) {
			const KArchiveEntry *entry = directory->entry(backupMagicFolder);
			if (entry->isDirectory()) {
				((const KArchiveDirectory*) entry)->copyTo(m_destFolder);
				m_success = true;
			}
		}
		tar.close();
	}
}

```

---

### Post by neilevan814 on 2010-02-03
Ok T4th

I didn't think about restoring the tar file manually.  Your suggestions have been successful.  I untar the backup manually and then from the applications restore window, I just use the option to restore an existing folder and it works.

Thank You very much for your help.

---

