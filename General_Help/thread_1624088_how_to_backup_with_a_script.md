---
title: "how to backup with a script?"
date: 2010-11-17
forum: General Help
---

### Post by machinakias on 2010-11-17
Hi all!
i need your help,please...
here it is what i need to do:

have a folder (/home/user/downloads) and i want to copy it as a tar.gz to a new folder named /home/user/backups.

i tried this

cp -R /home/user/downloads /home/user/backups
and it works,but if i change (e.g. add a file) the content of downloads,the next time it copies again all the files....
so i get double files!

the thing is that i need the script to check if there are changes in the downloads folder,so only the changes to be added...

got any ideas?

thank you!

---

### Post by oldfred on 2010-11-17
This post is what I used, change to your paths, I commented out the original examples and it has mine:

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh
Code:

#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

#rsync -auvP /home /media/backup
#rsync -auvP /share /media/backup
#rsync -auvP /media/floppy /media/backup
#rsync -auvP /etc /media/backup
echo "done"
exit 0

make it executable
Code:

chmod +x mybackup.sh

run it
Code:

./mybackup.sh

of course, do the dry run first as I said before
thank you very much. I made a symbolic link from /bin/backup to /root/backup.sh, thanks!!!!!

---

