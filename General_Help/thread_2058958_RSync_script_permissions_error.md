---
title: "RSync script permissions error"
date: 2012-09-17
forum: General Help
---

### Post by neanderslob on 2012-09-17
Hi all,

I'm trying to back up a remote server with RSync script:

```
#!/bin/bash

## my own rsync-based snapshot-style backup procedure

# config vars

SRC="goupsmar@go-upsmart.com:~/public_html/" #dont forget trailing slash!
SNAP="/media/Backups/UpSmart"
OPTS="-e ssh -rltgoi --delay-updates --delete --chmod=a-w"
MINCHANGES=20

# run this process with real low priority

ionice -c 3 -p $$
renice +12  -p $$

# sync

rsync $OPTS $SRC $SNAP/latest >> $SNAP/rsync.log

# check if enough has changed and if so
# make a hardlinked copy named as the date

COUNT=$( wc -l $SNAP/rsync.log|cut -d" " -f1 )
if [ $COUNT -gt $MINCHANGES ] ; then
   DATETAG=$(date +%Y-%m-%d)
   if [ ! -e $SNAP/$DATETAG ] ; then
      cp -al $SNAP/latest $SNAP/$DATETAG
      mv $SNAP/rsync.log $SNAP/$DATETAG
   fi
fi


```

However, when I run the script I get the following error.

> mv: cannot move `/media/Backups/UpSmart/rsync.log' to `/media/Backups/UpSmart/2012-09-17/rsync.log': Permission denied


When I checked the permissions on the directories the script created, they were automatically set so that no one could write to them, but instead only view them.  How do I resolve this?

---

### Post by neanderslob on 2012-09-17
I think I managed to solve this on my own.  I moved the chmod out of the rsync options and put it at the end of the ifstatement at the bottom.  This prevented the directory from being changed after everything was coppied to it, rather than before it was.

---

