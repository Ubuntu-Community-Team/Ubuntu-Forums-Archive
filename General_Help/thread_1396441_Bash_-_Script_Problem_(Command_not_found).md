---
title: "Bash - Script Problem (Command not found)"
date: 2010-02-02
forum: General Help
---

### Post by ushills on 2010-02-02
Hi,

Hoping someone can help

I have written the following script to backup my /home folder to an external hard-drive using rdiff-backup and want to use it on other machines hence the variables.

```
#!/bin/bash


# This script backs up the directory $BACKUPROOTDIR of the  
# localhost to themountpoint $BACKUPPATH on the server $SERVER using rdiff-backup.
# Incremental backups from the last $DURATIONTOKEEP days          
# are retained.                                                                                               
# Change the following variables to suit your machine

BACKUPROOTDIR="/home"					# root of filesystem to be backed up
DURATIONTOKEEP="60D"					# use the character D, W, M, or Y, indicating days,  weeks, months, or years respectively
BACKUPPATH="/media/WD/$HOSTNAME-backup/"
LOGFILE="/var/log/WD_home_backup.log"
EXCLUDEFILE="/home/ian/WDbackupexcludelist"
EXCLUDEEXPRESSION="/home/ian/WDbackupexcludeexp"

# Commence backup script 

# Check that rdiff-backup is installed
dpkg -l rdiff-backup | grep ii
if [[ $? == 1 ]]; then
aptitude install rdiff-backup
fi

# Set date in logfile
echo 'Start backup for 'date'\nBacking up' $BACKUPROOTDIR' to '$BACKUPATH >> $LOGFILE

# Check backup directory exists

if [ -d $BACKUPPATH]
	then
		echo $BACKUPPATH' used at destination'  >> $LOGFILE
	else 
		echo $BACKUPPATH' is not mounted'
		echo 'BACKUP FAILED'   >> $LOGFILE
		exit 1
fi

# List installed packages and write to backup destination
echo 'Writing install applications list to backup destination'
dpkg --get-selections | grep -v deinstall  > $BACKUPPATH/installed packages.list
echo 'Installed applications written to installed packages.list' >> $LOGFILE
echo 'SUCCESS'

# Copy sources.lst and write to backup destination
echo 'Writing sources.list to backup destination'
cat /etc/apt/sources.list > $BACKUPPATH/sources.list
echo 'Sources.list written to installed souces.list' >> $LOGFILE
echo 'SUCCESS'

# Check exclude file exists and warn if not

if [-e $EXCLUDEFILE]
	then
		echo 'exclude file' $EXCLUDEFILE ' used'
		echo 'files in' $EXCLUDEFILE ' omitted'  >> $LOGFILE
	else
		echo 'exclude file does not exist, backing up everything in' $BACKUPROOTDIR
		echo 'exclude file does not exist, backing up everything in' $BACKUPROOTDIR  >> $LOGFILE
fi

# Check exclude expression file exists and warn if not

if [-e $EXCLUDEEXPRESSION]
	then
		echo 'exclude expression file' $EXCLUDEEXPRESSION ' used'
		echo 'expressions in '$EXCLUDEEXPRESSION' omitted'  >> $LOGFILE
	else
		echo 'exclude expression file does not exist, backing up all file types in' $BACKUPROOTDIR 
		echo 'exclude expression file does not exist, backing up all file types in' $BACKUPROOTDIR  >> $LOGFILE
fi


cd $BACKUPROOTDIR

# Remove the expired incremental backups

echo 'Removing expired backups older than '$DURATIONTOKEEP
rdiff-backup --remove-older-than $DURATIONTOKEEP $BACKUPPATH
echo "SUCCESS"


# Write confirmation of purge expired incremental backups to logfile

echo 'Expired backups older than' $DURATIONTOKEEP ' removed.....SUCCESS'  >> $LOGFILE

#  Backup files and print stasticts to logfile

echo "Starting backup"
rdiff-backup --print-statistics --exclude-filelist $EXCLUDEFILE --exclude-regexp $EXCLUDEEXPRESSION $BACKUPROOTDIR $BACKUPPATH >> $LOGFILE
echo "Backup completed"

# Write confirmation of backup completion to logfile
echo "Backup 'date'.....SUCCESS\n----------" >> $LOGFILE

# Verify files
echo 'Verifying files'
rdiff-backup --verify $BACKUPPATH  >> $LOGFILE
echo 'Verify complete'






```

However when I execute it I keep getting the error Command not found and $/r.

Have I got it all wrong.

I changed permission using

```
sudo chmod 700 backup.sh
```

and execute the script with

```
./backup.sh
```

---

### Post by geirha on 2010-02-02
There are several things wrong with this script.

1. It's missing the she-bang, which should be #!/bin/bash, since you are using bash-specific features. (make sure first line reads #!/bin/bash)

2. «dpkg -l rdiff-backup | grep ii», you should be more interested in knowing if there is an rdiff-backup command in PATH, which you can use the command-builtin for. Also a return value of 1 is indeed a "false" value. But so is 2, 3 ... 255. So only checking if $? = 1 is a bad idea.
```

if ! command -v rdiff-backup >/dev/null; then 
    echo "rdiff-backup not avilable. Please install it." >&2
    exit 1
fi
```

3. «if [ -d $BACKUPPATH]»  [ is a command. And as any other command, each argument must be separated by whitespace (] is an argument, and it needs to be the last argument of the [-command). Secondly, $BACKUPPATH is not quoted (in double quotes "$BACKUPPATH"), so if it contains spaces or globs, you may get an error, and the [-command return false even if the directory exists. Thirdly, in bash you should use the improved [[-keyword instead of the [-command. Since [[ is not a command, but a keyword, it can deal with variables without requiring quotes. So
```
if  [[ -d $BACKUPPATH ]]; then ...
# or, if you want to write for POSIX shell instead of bash
if [ -d "$BACKUPPATH" ]; then ...
```

4. «cd $BACKUPROOTDIR» - Even if the dir exists and doesn't contain spaces, cd may fail (due to permission problems, or some other program could've deleted it just before this command). Good practice dictates that you always check the return value of cd. And again, "quote" it! ```
cd "$BACKUPROOTDIR" || exit
```

Lastly, the convention is to use lowercase variable names. UPPERCASE variable names are used for internal shell variables and environment variables. Using lowercase variable names ensures that you don't accidentaly override any of those.

---

### Post by ushills on 2010-02-02
Would this be correct now.

```
#!/bin/bash

# This script backs up the directory $backuprootdir of the  localhost to the
# mountpoint $backuppath on the server $SERVER using rdiff-backup. 
# Incremental backups from the last $durationtokeep days
# are retained. 

# Change the following variables to suit your machine

backuprootdir="/home"					# root of filesystem to be backed up
durationtokeep="60D"					# use the character D, W, M, or Y, indicating days,  weeks, months, or years respectively
backuppath="/media/WD/$HOSTNAME-backup/"
logfile="/var/log/WD_home_backup.log"
excludefile="/home/ian/WDbackupexcludelist"
excludeexpression="/home/ian/WDbackupexcludeexp"

# Commence backup script 

# Check that rdiff-backup is installed
if ! command -v rdiff-backup >/dev/null; then 
    echo "rdiff-backup not avilable. Please install it." >&2
    exit 1
fi

# Set date in logfile
echo 'Start backup for 'date'\nBacking up' $backuprootdir' to '$BACKUPATH >> $logfile

# Check backup directory exists

if [[ -d $backuppath ]];
	then
		echo $backuppath' used at destination'  >> $logfile
	else 
		echo $backuppath' is not mounted'
		echo 'BACKUP FAILED'   >> $logfile
		exit 1
fi

# Check directory to backup is accessible to user

cd "$backuprootdir" || exit

# List installed packages and write to backup destination
echo 'Writing install applications list to backup destination'
dpkg --get-selections | grep -v deinstall  > $backuppath/installed packages.list
echo 'Installed applications written to installed packages.list' >> $logfile
echo 'SUCCESS'

# Copy sources.lst and write to backup destination
echo 'Writing sources.list to backup destination'
cat /etc/apt/sources.list > $backuppath/sources.list
echo 'Sources.list written to installed souces.list' >> $logfile
echo 'SUCCESS'

# Check exclude file exists and warn if not

if [-e $excludefile]
	then
		echo 'exclude file' $excludefile ' used'
		echo 'files in' $excludefile ' omitted'  >> $logfile
	else
		echo 'exclude file does not exist, backing up everything in' $backuprootdir
		echo 'exclude file does not exist, backing up everything in' $backuprootdir  >> $logfile
fi

# Check exclude expression file exists and warn if not

if [-e $excludeexpression]
	then
		echo 'exclude expression file' $excludeexpression ' used'
		echo 'expressions in '$excludeexpression' omitted'  >> $logfile
	else
		echo 'exclude expression file does not exist, backing up all file types in' $backuprootdir 
		echo 'exclude expression file does not exist, backing up all file types in' $backuprootdir  >> $logfile
fi


cd $backuprootdir

# Remove the expired incremental backups

echo 'Removing expired backups older than '$durationtokeep
rdiff-backup --remove-older-than $durationtokeep $backuppath
echo "SUCCESS"


# Write confirmation of purge expired incremental backups to logfile

echo 'Expired backups older than' $durationtokeep ' removed.....SUCCESS'  >> $logfile

#  Backup files and print stasticts to logfile

echo "Starting backup"
rdiff-backup --print-statistics --exclude-filelist $excludefile --exclude-regexp $excludeexpression $backuprootdir $backuppath >> $logfile
echo "Backup completed"

# Write confirmation of backup completion to logfile
echo "Backup 'date'.....SUCCESS\n----------" >> $logfile

# Verify files
echo 'Verifying files'
rdiff-backup --verify $backuppath  >> $logfile
echo 'Verify complete'


```

---

