---
title: "Improving my backup script"
date: 2012-09-12
forum: General Help
---

### Post by Erik1984 on 2012-09-12
Here is the script I currently use:

```

#!/bin/bash
#globals:
mntpnt="/media/BackupPartition"
sourcefolder1="/home/myname/"
sourcefolder2="/media/WindowsPartition/"
targetfolder1="/media/BackupPartition/HomeBackup"
targetfolder2="/media/BackupPartition/WinDataBackup"

options1="-av --exclude-from=/home/myname/scripts/exclude_file1.txt"
options2="-av --exclude-from=/home/myname/scripts/exclude_file2.txt"
outputfile="/home/myname/backuplog.txt"
errormessage="Backup medium not mounted. Cannot perform backup."
succesmessage="A backup has been made."
deleteCommand=""

function writeLog {
    echo "$1" >> $outputfile 
}

function displayPopup {
    notify-send "$1"    
}

function writeHeader {
    writeLog "##########################################"
    writeLog "Date: $(date)"
}

function doSync {    
    #write stuff to log
    rsync $options1 $deleteCommand $sourcefolder1 $targetfolder1
    if [ $? -eq 0 ]; then
        #write to log
    else
        #write to log
    fi
    writeLog "Begin backup windata"
    rsync $options2 $deleteCommand $sourcefolder2 $targetfolder2
    if [ $? -eq 0 ]; then
        #write to log
        displayPopup "${succesmessage}"
    else
        #write to log
    fi
}

writeHeader
if [ $# -eq 1 ]; then
    if [ $1 == "--delete" ]; then
        deleteCommand="--delete"
        writeLog "Use the --delete option."
    else
        writeLog "Unknown argument: "$1", ignored."
    fi
else
    writeLog "Do not use --delete option."
fi
if mountpoint -q $mntpnt; then            
    doSync
else    
    #write to log
    displayPopup "${errormessage}"
fi

```What is does is rsync two folders to an external harddrive. One folder is my /home/user and the other one is a NTFS mount where most of my personal data is stored (documents, photos, music etc.). Furthermore it shows a popup when the rsync commands are done. This works but I'd like some feedback. Any tips on making the code more efficient maybe?

Finally I have a question on the mount part of the script. On Ubuntu the backup partition gets automatically mounted when I plug the external harddrive but this was not the case on Kubuntu. To make the script more 'robust' I would like to check if the partition is available for mounting and mount it in the script if the partition is not mounted already.

---

### Post by Zimmer on 2012-09-12
Replacing backuplog.txt     with  $(date +%Y%m%d)_backup.log
in
outputfile="/home/myname/backuplog.txt"

would give you a dated logfile eg 20120912_backup.log .

EDIT: provided you put it in the rsync options: as --log-file=/home/myname/$(date +%Y%m%d)_backup.log

However, the use of quotes for the string variable declaration will probably need to be modified to "QUOTE" the variable $(date +%Y%m%d)

(and I forget how to do that, offhand, as it has been a long time since I actually wrote anything.. :)   )

---

### Post by Erik1984 on 2012-09-13
Thanks Zimmer. I didn't know about the log-file option for rsync, seems like a good idea to create a log per date. 

Do you also know how I could mount (from inside the script) the backup partition when it is not mounted yet ?

---

### Post by Erik1984 on 2012-09-14
*bumps topic for the mount part*

---

### Post by oldfred on 2012-09-14
Mine is a fixed disk partition, not sure how this all works as I just copied it from some other thread.  If external disk, it may not always be the same drive? I would then research mounting by label.

```
# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

```

---

