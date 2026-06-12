---
title: "Back in Time snapshot problem"
date: 2012-05-23
forum: General Help
---

### Post by Falc7 on 2012-05-23
I have been using the program 'back in time' to create backups of my home partition. I successfully made two snapshots before now. Recently however I cant take any new snapshots, it says:
Error: Failed to take snapshot
It provides no more information than that, is there anyway I can find out what is wrong and fix it?

---

### Post by Sidewinder1 on 2012-05-23
I've never used the "Back-in-Time" program so I can't really help you troubleshoot it, sorry. That being said, for backup purposes I have always used "Grsync." It is a gui based program that simply uses the rsync command but allows you to select all of the options that you want without all of the syntax knowlege necessary for command line commands.

HTH,
Side

---

### Post by Falc7 on 2012-05-23
Okay thanks i'll look at that program, i got some output from the terminal that may help explain whats going wrong:

```
Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.

INFO: Lock
INFO: on process begins
INFO: Profile_id: 1
INFO: Call rsync to take the snapshot
WARNING: Command "rsync -rtDH --links --no-p --no-g --no-o  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="/media/Expansion Drive/Backups" --exclude="/home/jamie/.local/share/backintime" --include="/home/jamie/" --include="/home/" --exclude=".gvfs" --exclude=".cache*" --exclude="[Cc]ache*" --exclude=".thumbnails*" --exclude="[Tt]rash*" --exclude="*.backup*" --exclude="*~" --exclude="/home/jamie/Ubuntu One" --exclude=".dropbox*" --exclude="/home/jamie/.thunderbird" --exclude="/home/jamie/.wine/drive_c/Program Files/Steam" --exclude="/home/jamie/.wine/dosdevices/c:/Program Files/Steam" --exclude="/home/jamie/Torrents" --exclude="/home/jamie/VirtualBox VMs" --include="/home/jamie/**" --exclude="*" / "/media/Expansion Drive/Backups/backintime/jamie-Inspiron-N5010/root/1/new_snapshot/backup/" 2>&1" returns 5888
INFO: Command "find "/media/Expansion Drive/Backups/backintime/jamie-Inspiron-N5010/root/1/new_snapshot" -type d -exec chmod u+wx {} \;" returns 0
INFO: Command "rm -rf "/media/Expansion Drive/Backups/backintime/jamie-Inspiron-N5010/root/1/new_snapshot"" returns 0
INFO: Command "rm -rf "/media/Expansion Drive/Backups/backintime/jamie-Inspiron-N5010/root/1/20120523-212244-162"" returns 0
ERROR: Failed to take snapshot !!!
INFO: Unlock


```

---

### Post by Sidewinder1 on 2012-05-24
OK; by your post above it would appear that "backintime" does essentially the same as "Grsync." That is, uses the rsync command. I would assume that you set all of the various 'exclude' and 'include' parameters, as well as what to delete (the rm rf inputs), etc.? Not including any data that you may have on external drives, all that you really need to back up is what's in the /home directory as all of the programs in / , were either installed by default with the os, or added by you with apt-get or one of the pkg. mgt. tools and are therefore readily available for reinstall/re-download if you ever need them.
Also, in the 'exclude' list are various files that are recreated, new, each time you boot and do not need to be backed up. Probably one of the most important files to 'exclude' is the backup file itself as it would start an infinite loop/fork-bomb type of thing. You know, like backing up the backup file, which has now changed and needs to back up the back up...  I hope that makes sense. Here is a link that lists several back up proceedures, should you continue to have problems with "backintime"/"Grsync": [https://help.ubuntu.com/community/jmburgess/Backup](https://help.ubuntu.com/community/jmburgess/Backup)

HTH,
Side

---

### Post by Falc7 on 2012-05-29
How do you exclude files in grsynch?

---

