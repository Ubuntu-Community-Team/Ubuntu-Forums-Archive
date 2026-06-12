---
title: "ubuntu linux copy all files from folder with extension including subfolders in a cron"
date: 2012-01-04
forum: General Help
---

### Post by the1joker on 2012-01-04
Hello,
 
I've been working with cronjobs and now im looking to automatically backup the files in my www/domain/, but there are a lot of files not needed that would just take up a lot of space, like the images and such. 
 
Lets say i would want to only copy the files from my root folder (and its subfolders) with the extensions .php and .inc, is that possible??
 
i would want that every hour, and then i a folder with the date added to it...
 
would my cron look anything like this??
 
date= `date -I`;
5 * * * * cp /home/tobias/www/sb/ /home/tobias/www/backup/sb$date/
 
i mean i know that simple line would work, but it needs something added i guess. So i need it to filter to only .php and .inc files, but keep a filestructure, so if these files are currently in subfolders those would need to be created or copied too.... 
 
What would i add and where or change of course?
 
Thank you in advance!

---

### Post by yotam on 2012-01-06
Not tested, but hopefully the following script,or some minor variant of it can do the desired job.

```
#!/bin/bash

datei=$(date -I)
cd /home/tobias/www/sb
tar -c -f - $(find . -name '*.inc' -o -name '*.php') | \
  tar -C /home/tobias/www/backup/sb${datei} -x -f -
```

---

### Post by the1joker on 2012-01-11
hey sorry for the late reply, been out nof town, thanx so much for the response, it seems a lot like i need, only i have a question about the structure.
 
 
If i copy it exactly it doesnt work in my cron, i didnt expect it but this is what i have::
 
sudo crontab -e gives :
#!/bin/bash
datei = $(date -I)
59 12 * * * cd /home/tobias/www/sb tar -c -f - $(find . -name '*.inc' -o -name '*.php) | \ tar -C /home/tobias/www/backup/sb&{datei} -x -f -
 
 
i know i am doing something wrong but.. not familiar enough with it to get it setup...
 
coul.d you give me another kick in the right direction??

---

### Post by cryptotheslow on 2012-01-11
You would need to put yotam's script into a file (use any text editor - gedit / nano etc). Mark that file as executable (chmod +x or use the file properties dialogue in Nautilus). Then call that newly created file from crontab.

Actually - having created the file and made it executable you could run it from the terminal prompt to see if it does what you expect before scheduling it up with cron.

I've not looked in any detail at yotam's script so no idea if it will do what you want - just advising how to get it into executable script form :)

Personally I would elect to use rsync for such a task. I have a couple of scripts kicking around on another box that do something similar to what you want - I'll dig them out and post them up for reference if you'd like?

---

### Post by the1joker on 2012-01-11
Yes Please, if there are better ways of backing up my development its appreciated.
 
Thanks for the reply, and explanation, im going to try yotam's, but wouldnt mind learning other ways /scripts as well!!

---

### Post by the1joker on 2012-01-11
#!/bin/bash
datei=$(date -I)
cd /home/tobias/www/sb
mkdir /home/tobias/www/backup/sb${datei}
tar -c -f - $(find . -name '*.inc' -o -name '*.php') | \
  tar -C /home/tobias/www/backup/sb${datei} -x -f -
 
 
Thats it Working!!!!!
Thanks guys, but yeah id still apreciate the chance to further this, and to learn it in other ways, so i hope you can still get me the other script..

---

### Post by cryptotheslow on 2012-01-11
Hmm - re-reading your OP what I have is not really going to do the job.

This one maintains a weeks worth of daily backups (once a day my webserver ftps the backup into /home/ftpuser/upload/daily) - this script runs once a day and copies the daily backups out to separate folders named Mon - Sun.

```

#!/bin/sh

# This script rotates the backup files daily, keeping 7 days worth.

DATEFORMAT=$(date +%a)
BACKUPSOURCE=/home/ftpuser/upload/daily
BACKUPDEST=/home/ftpuser/upload/rotation/

rm -Rf $BACKUPDEST/$DATEFORMAT
mkdir $BACKUPDEST/$DATEFORMAT
cp -R $BACKUPSOURCE/* $BACKUPDEST/$DATEFORMAT

chmod -R 755 $BACKUPDEST

```

As for rsync that would be more suitable if you wanted to keep a backup copy location in sync with your live environment. One benefit of rsync is that it only copies files that have changed - particularly useful for a remote backup scenario as it can use SSH to communicate over as well as reduce the amount of data transferred.

e.g. I use it to maintain a copy of some folders from my desktop PC onto my little server on the LAN. This one maintains a copy of  /media/2ndDrive/backups for example

```
#!/bin/sh
echo "Backing up backups folder to ubuserver!"
rsync -r -a -c -v --delete -e ssh /media/2ndDrive/backups crypto@ubuserver:~/desktopbackups/2ndDrive
read -p "Done. Waiting here for the boss-man to see me and hit a key!" nothing
```You probably want to **man rsync** to get a grip with its various options - one wrong option and it's quite possible to end up emptying what you intended to be the source directory rather than updating the intended destination. :) Also the above is meant to be run as an interactive script rather than cronned - to cron it would require some messing around setting up keyfiles and the like for the SSH connection to "ubuserver".

Just some food for thought - applicable or not :D

---

### Post by btindie on 2012-01-11
> **the1joker said:**
> Thanks guys, but yeah id still apreciate the chance to further this, and to learn it in other ways, so i hope you can still get me the other script..

With rsync you can do something like the following

```

mkdir -p /home/tobias/www/backup/sb$(date +%F)
rsync --progress -avh --prune-empty-dirs --include '*/' --include='*.php' --include='*.inc' --exclude='*' \
/home/tobias/www/sb/ /home/tobias/www/backup/sb$(date +%F)/

```You can use the -n option with rsync to see what it would do without it actually making any changes.

That will then only copy the new files to the backup directory. You'll then need a daily script to delete/move backups that are older than a certain number of days.

---

### Post by the1joker on 2012-01-11
Thanks ill try it out, and yeah i would prefer to just backup the changed files of course. that would be better, ill play around with it though, thanks every1 for your thoughts!

---

