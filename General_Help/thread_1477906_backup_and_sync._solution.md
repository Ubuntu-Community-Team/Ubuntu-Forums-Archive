---
title: "backup and sync. solution"
date: 2010-05-09
forum: General Help
---

### Post by camaron1 on 2010-05-09
This is what I'm looking for:

I want to choose what folder(s) to backup to an external usb hard-drive. Once the initial backup has been completed the backup software should work as a daemon so it is alert as to when some file is changed and ONLY backup this. So if I delete some files from a folder the same files get deleted from the external drive. If I tag some music file the same file gets updated on the external drive. I think you get the idea. Dropbox does all this in a small scale and on the cloud. Is there such a thing?

Thanks in advance.

---

### Post by darthrax on 2010-05-09
Hi,

just paste the following in a file, make the file executable, set it up in scheuled tasks and you've got your deamon...(each script should be in a different file)

If your files are all over the place use this script. (it'll create a path like /media/backup/path/to/folder1)
```

#!/bin/bash
for folder in /path/to/folder1 /path/to/folder2 "/path/to folder/with a space in the name use quotes" /path/to/foldern
do
rsync -aPzvv --delete "$folder"/ /media/backup/"$folder"/
done

```

If your files are in one place like your home directory for example then use this script. (it'll create a path like /media/backup/folder1)
```

#!/bin/bash
for folder in folder1 folder2 "folder 3" foldern
do
rsync -aPzvv --delete ~/"$folder"/ /media/backup/"$folder"/
done

```

If you want an hourly backup of your work files like what time machine does for Macs use this script. Change the folder options (paths/names) to suit your situation and dont forget to change the source path at the rsync command(the $folder vs /path/to/$folder). This will create an incremental backup with a path like /media/backup/path/to/folder/Backup-16-08-14 (backup taken at 04:08:14 PM). The first backup from yesterday will be recycled into the first backup for today (total 24 hours) and all changes will be propogated from the previous backup (1 hour ago in this case). This saves time by not deleting and recreating the backup image. The total space taken up by all the folders will be the first backup + changes since first backup.
```

#!/bin/bash
for folder in /path/to/folder1 /path/to/folder2 "/path/to folder/with a space in the name use quotes" /path/to/foldern
do
date=$(date "+%H-%M-%S")
date1=$(date --date="1 hour ago" "+%H-%M-%S")
date24=$(date --date="24 hour ago" "+%H-%M-%S")
mv /media/backup/"$folder"/Backup-$date24 /media/backup/"$folder"/Backup-$date
cp -al /media/backup/"$folder"/Backup-$date1/. /media/backup/"$folder"/Backup-$date
rsync -aPzvv --delete "$folder"/ /media/backup/"$folder"/Backup-$date/
done
```

Install task scheduler from the ubuntu software center and set the script up as a cron job. you can call it hourly or daily or however often you want. The first backup will take time after that it'll be a breeze.

Hope this helps...i just wrote the daily backup script for my server and its currently making the first backup...enjoy.:)

---

### Post by camaron1 on 2010-05-09
Hey, thanks for that... :)

I'm off just now but I'll give it a try tonight. 

Thanks again

---

### Post by camaron1 on 2010-05-23
I have since discovered **Back in time** which is a front end for rsync. It is very simple to use and does a very good job.

---

