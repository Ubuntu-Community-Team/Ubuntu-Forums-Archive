---
title: "Can't run script using sudo"
date: 2010-12-21
forum: General Help
---

### Post by Jense on 2010-12-21
Hi,

I wrote a script to backup data from one server to another. Today I noticed that the script isn't working when called by a cronjob. So testing I noticed that, though 
```
notroot@ubuntu:~/backup$ ./backupDev.sh

``` works, the same thing does not work when run as sudo
```
notroot@ubuntu:~/backup$ sudo ./backupDev.sh 
./backupDev.sh: 14: Syntax error: "(" unexpected

```
or 
```

notroot@ubuntu:~$ sudo /home/notroot/backup/backupDev.sh
/home/notroot/backup/backupDev.sh: 14: Syntax error: "(" unexpected

```

I really have no idea why this isn't working. Below you can see the script:

```


#!/bin/bash

# Define the host server
HOST=xxx.xxx.xxx.xxx

# Define the host user
USER=backup

# Define path for rsync.sh
RSYNC_PATH=/home/notroot/backup

# Define Array for source directories
SRC_DIR=('/home' '/var/www' '/etc')


# Define remote path for archive script
ARCHIVE_SCRIPT="/media/storageRunds/backup/archiveBackup.sh dev"


# Define backup destination base directory


# Get number of elements in the BACKUP_DIR array
ELEMENTS=${#SRC_DIR[@]}

# Define date
THEDATE=`date '+%d%m%Y'`

# Define sync direcotry
SYNC_DIR=/media/storageRunds/backup/dev/sync_dir


for (( i=0;i<$ELEMENTS;i++)); do
   rsync -avz -e "ssh -p 10022" ${SRC_DIR[$i]} $USER@$HOST:$SYNC_DIR/
#$RSYNC_PATH/rsync.sh run push $SRC_DIR $USER $HOST $SYNC_DIR 22
   echo 'done the rsync on '${SRC_DIR[$i]}
done


ssh -p 10022 $USER@$HOST $ARCHIVE_SCRIPT



```

---

### Post by DaithiF on 2010-12-21
it sounds like sudo is invoking /bin/sh rather than /bin/bash to run the script.

as an experiment try:
```
sudo -s /bin/sh yourscript

```and
```
sudo -s /bin/bash yourscript
```

and you'll probably find that the first fails with the error you posted and the second succeeds.

From what you posted i don't see why this would be happening though ... the  #!/bin/bash shebang should result in bash being used.  maybe something in that shebang line not quite right -- windows line ending perhaps?

---

### Post by Dave_L on 2010-12-21
Shouldn't there be a space between the "i++" and the right parenthesis?

Also, the "x" option may provide more information:

sh -x script.sh

---

### Post by Jense on 2010-12-21
Thanks a lot DaithiF, sudo was indeed using the wrong shell. Invoking the script with /bin/bash did word.

And yes, there should be a space, but it seems bash is forgiving that minor mistake.

Thanks, that issue is solved.

---

### Post by Jense on 2010-12-22
In case anybody else stumbles over this, both the above solutions worked. Seems that /bin/bash is more forgiving about missing spaces then /bin/sh

Cheers

---

