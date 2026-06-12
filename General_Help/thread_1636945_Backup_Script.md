---
title: "Backup Script"
date: 2010-12-03
forum: General Help
---

### Post by vaniaspeedy on 2010-12-03
Hey, I hope this is the right forum, if not; my apologies, mods feel free to move it.

I had some extra time today, and decided to write a small script to backup up an ubuntu installation. I know many people have problems backing up their systems often enough, so I hope this will help.

This is a three part script;
baksys.sh is the actual backup solution
watch.ls.sh is a tiny script that will monitor the growth of the tgz file
restoresys.sh will restore your system

-----------------------------------------------------------------------------------------
baksys.sh

```
#!/bin/sh
## part one of a three script pack, backup restore and watch.

##Backup script by Vania S.

##calling variables to create filename.
 
TODAY=$(date +"%m-%d-%y")

HOST=$(hostname)

DISTRO=$(
cat /etc/*-release > name.txt
cut -d'=' -f2- name.txt >name2.txt
sed '3!d' name2.txt
rm name.txt name2.txt
)

filename="$HOST.$DISTRO.$TODAY.tgz"

## tellling user what's up
echo "---------------------------------------------------------------"
echo "Date: $TODAY    Distro: $DISTRO                Host:$HOST      "
echo "Creating a backup tgz file in the same location as this script."
echo "---------------------------------------------------------------"
echo "run watch.ls.sh in a new window to monitor the file growth."
echo "This script will resume in 15 seconds."
sleep 15

## actual backup command
tar cvpzf $filename --exclude=/proc --exclude=$filename --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
echo "---------------------------------------------------------------"
echo "Done!"
echo "When you want to restore, put the tgz in the same folder as the"
echo "scripts, and run restoresys.sh"
```--------------------------------------------------------------------------------------
watch.ls.sh
```

#!/bin/sh
## part two of a three script pack, backup restore and watch.

##Watch script by Vania S.

HOST=$(hostname)
watch -d -n 1 -d ls -lh $HOST*.tgz

```--------------------------------------------------------------------------------------
restoresys.sh
```

#! /bin/sh
## part three of a three script pack, backup restore and watch.

##Restore script by Vania S.


HOST=$(hostname)

## start script

su
cd /
tar xvpfz $HOST*.tgz -C /
mkdir proc media lost+found mnt sys

```--------------------------------------------------------------------------------------

Additional info
    You can integrate these scripts into your system, and turn them into commands. 
1.Move them to /bin
2. Remove the .sh extension
3. Make them executable 
```
chmod +x baksys restoresys watch.ls
```4. Voila! Now you can run these commands from the terminal, just make sure to be root.

Optional
   Change the backup script so that the file is saved on a separate partition, example:
Original:
```
tar cvpzf $filename --exclude=/proc --exclude=$filename --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
```New:
```
tar cvpzf /YOUR/MNT/POINT/$filename --exclude=/proc --exclude=$filename --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
```Please post comments and suggestions, I'm curious to see how it goes.
            Vania S.

---

