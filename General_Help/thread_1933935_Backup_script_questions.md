---
title: "Backup script questions"
date: 2012-03-01
forum: General Help
---

### Post by MadsRC on 2012-03-01
I have created this script from ubuntu wiki pages:
> #!/bin/bash
# Backup Script
#
#What to backup.
backup_files="/home/mrc/"
#Where to place backup.
dest="/home/mrc/backup/"
#Create archive filename.
day=$(date +%d%m%Y-%R)
hostname=$(hostname -s)
archive_file="$hostname-$day.tgz"
#Print start status message.
echo "Backing up $backup_files to $dest/$archive_file"
date
echo
#Backup the files using tar.
tar czf $dest/$archive_file $backup_files --exclude 'backup/*' --exclude 'backup'
#Print end status message.
echo
echo "Backup finished"
date
#Long listing of files in $dest to check file sizes.
ls -lh $dest
My question is however, how to I get rid of this line when I run the script:
> tar: Removing leading `/' from member namesThe script is successfull. BUT I'm getting tired of that line...

---

### Post by kevdog on 2012-03-01
I know this doesn't really answer your question, but I'd give up on the method you're trying to develop and jump to rsync. You can exclude directories with this method.  rsync has been used and developed for years and is made with one purpose in mind -- backups.

---

### Post by Khayyam on 2012-03-01
> **MadsRC said:**
> I have created this script from ubuntu wiki pages [...] My question is however, how to I get rid of this line when I run the script:
> tar: Removing leading `/' from member namesThe script is successfull. BUT I'm getting tired of that line...

skip long digression about the use of '-P' and the removing of the leading slash .. yadda-yadda.

Ugly little script, '-C' should fix it ... here's the 'braceified' version

```
#!/bin/bash

BACKUP_FILES="${HOME}/prj/"
DEST="${HOME}/backup/"
DAY=$(date +%A)
HOSTNAME=$(hostname -s)
ARCHIVE_FILE="${HOSTNAME}-${DAY}.tar.gz"

echo "Backing up $BACKUP_FILES to ${DEST}/${ARCHIVE_FILE}"
tar czf ${DEST}/${ARCHIVE_FILE} -C ${BACKUP_FILES}
echo "Backup finished"
```HTH ... khay

---

### Post by MadsRC on 2012-03-01
Thank you Khay.

I'm learning Bash, I know it could be prettier ;)

However, executing that script yields:
> Backing up  to /home/mrc/backup//mrc-Thursday.tar.gz
tar: option requires an argument -- C
Try `tar --help' or `tar --usage' for more information.
Backup finished

---

### Post by Khayyam on 2012-03-01
> **MadsRC said:**
> Thank you Khay.

I'd say "your welcome" had I got it right first time ... so, now having tested it

```
#!/bin/bash

BUP_FILES_DIR="prj"
DEST="${HOME}/backup"
ARCHIVE_FILE="$(hostname -s)-$(date +%F).tar.gz"

echo "Backing up ${HOME}/${BUP_FILES_DIR} to ${DEST}/${ARCHIVE_FILE}"
tar -C ${HOME} -czf ${DEST}/${ARCHIVE_FILE} ${BUP_FILES_DIR}

if [[ $? == 0 ]]; then
    echo ""
    echo "Backup finished"
else
    echo ""
    echo "There was a problem completing the backup"
fi
```Note I've changed "date +%A" to "date +%F" ... which seems a little more informative ... you can obviously change it back if you so wish.

best ... khay

---

### Post by MadsRC on 2012-03-01
Thank you :)

Found a problem with it though. tar gives an I/O error when untar'ing the backup file created. Both on my server and if I download it to my local pc... Untar'ing it with the gui works though...

Solved it by chaning the time format from ":" to "_"

Used your code to modify my existing, will post it when it's done :D

---

### Post by Khayyam on 2012-03-01
> **MadsRC said:**
> Thank you

Your welcome ...

> **MadsRC said:**
> Found a problem with it though. tar gives an I/O error when untar'ing the backup file created. Both on my server and if I download it to my local pc [...] solved it by chaning the time format from ":" to "_".

The date format 'date +%F' is "-" (dash) seperated, there should be no problem with dashes.

> **MadsRC said:**
> Used your code to modify my existing, will post it when it's done.

OK ... best ... khay

---

### Post by MadsRC on 2012-03-01
Ah sorry, It was actually my own code that messed it all up.

 Think I got it now :P Wouldn't learn anything if I didn't break stuff :D

---

