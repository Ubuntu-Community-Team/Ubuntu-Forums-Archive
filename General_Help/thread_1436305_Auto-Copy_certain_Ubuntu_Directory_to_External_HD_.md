---
title: "Auto-Copy certain Ubuntu Directory to External HD (Backups)"
date: 2010-03-22
forum: General Help
---

### Post by Peter Alien on 2010-03-22
I need once a day at a specific hour, to copy a specific directory (that has my professional files) in Ubuntu 9.10 to an external HardDisk that is formatted as NTFS.
And i have to give it each time a diferent name to avoid overwrite directories that just exists in that external HD.
(It's my backup HD)

Can someone tell how i can do that in Karmic Koala?
Is it possible to automate this action, i could always copy/paste that directory to external HD, but if it was possible to automate this situation it could be better?

Thank you.

---

### Post by TitanusEramius on 2010-03-22
Have you looked at rsync to do this?
Type
```
man rsync
```in the terminal to read about rsync.

The automated part can be done with crontab, or maybe crontab and a custom script, but I can't help you with that part since I can't get my own rsync to work with crontab :) To read more about crontab just type
```
man crontab
```in the terminal.

Rsync also comes with a gui:
[http://www.opbyte.it/grsync/screenshot.html](http://www.opbyte.it/grsync/screenshot.html)

Good luck

---

### Post by Peter Alien on 2010-03-24
Thank you TitanusEramius.

I'll read the manual for rsync.

---

### Post by Peter Alien on 2010-03-28
My real ideia is to put the command above in "Cron" to create an automatic backup of a Folder where i have my important files in Ubuntu, at 1 p.m., everyday (monday to friday), in an USB external HD formatted as NTFS or FAT32:

tar -cvjf /Destiny Folder/Filename_$(date +%Y%m%d).tar.bz2 /Origin Folder/



To put this in Cron how can i do it... can i use Crontab.. how can i put it into Cron's table?


And what can i do for Ubuntu 9.10 mount automaticaly this USB external HD when Ubuntu starts?



Many thanks in advanced.

---

### Post by Peter Alien on 2010-03-29
Well this is what i have done:

i created a script called "autobackup":

#!/bin/bash
sudo mount /dev/sdc1 /home/xxxxx/mount_hd
tar -cvjf /home/xxxxx/mount_hd/Backups/backup_$(date +%d%m%Y)_$(date +%H%M%S).tar.bz2 /home/xxxxx/ImportantFolder
sudo umount /dev/sdc1


and i used cron, with crontab -e:

00 12 * * 1-5 /home/xxxxx/bin/autobackup


The only problem is that the TAR.BZ2 file includes the directories "home", "xxxxx" and "ImportantFolder", and i only want to include the last directory and the files inside it.

One thing more the compressed file includes too, files like xxx~,
i think those files with ~ are temporary files or security files, and my Ubuntu is always creating them.
Can anyone tell me how can i stop Ubuntu from creating this files, because they also get inside the TAR.BZ2 file.

Many thanks in advanced.

---

### Post by oldfred on 2010-03-29
Cannot help on tar, but you mentioned FAT.

For at least 2 years I ran a manual backup using the simple backup and had some space in the FAT partition so I put it there. I always thought my backup was 4GB. But 4GB is the max size for a file in FAT, so when I changed to a ext3 partition my backup was two or three times larger. I never had a back up  and only thru luck it did not need it. If you need windows compatibility use NTFS otherwise ext3.

---

### Post by Peter Alien on 2010-03-30
i wanted FAT32 or NTFS (this last one is my favorite).

I'm using Ext4 with Journal in my Ubuntu machine (i think it's better than Ext3).

About the ~ stuff, i found out that some Apps in Linux produce annoying backup files (with ~ in its names)... unfortunately the "autobackup" script captures them :( Is there a way to avoid that?

---

