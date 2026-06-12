---
title: "cp command inconsistency"
date: 2010-01-07
forum: General Help
---

### Post by dasbrow on 2010-01-07
I'm trying to copy (cp) a few directories to a small HD that I have added to my system.  It is a back-up of sorts.  I delete the previous /Backup directory and then use cp to recreate it and populate it with the current files.  The cp command does not create the subdirectory for the first few lines but does for the last few lines.  If I execute the cp lines manually in the terminal, they work fine.  Here is my bash script:

#!/bin/bash

sudo rm -v -R /media/backup/Backup

sudo cp -v -R /home/dino/Documents      /media/backup/Backup
sudo cp -v -R /home/dino/Pictures       /media/backup/Backup
sudo cp -v -R /home/dino/.wine/drive_c/data     /media/backup/Backup
sudo cp -v -R /home/dino/.mozilla       /media/backup/Backup
sudo cp -v -R /home/dino/.mozilla-thunderbird   /media/backup/Backup

I would expect to find a .../Backup/Documents directory in the new location as well as a .../Backup/Pictures directory there.  Instead, the contents of the two directories are just dumped in the .../Backup directory.

The last three lines create the expected new subdirectories, in this case: /data; /.mozilla; and, /.mozilla-thunderbird.

If I move the last two lines of the script to the beginning of the cp command lines, the subdirectories will not be created.  But, the subdirectories for the rest of the lines WILL be.

What is it about the first two cp commands that allows them to produce a different result from the following cp lines?  How can I fix it?

Thank you.

---

### Post by mdurham on 2010-01-07
Just guessing here, maybe it's because the Backup dir doesn't exist.
Instead of deleting it try just deleting it's contents.

sudo rm -v -R /media/backup/Backup/*

cp -v -R blah...blah...blah

---

### Post by john newbuntu on 2010-01-07
On a slightly related note, explore the "rsync" command if you are creating backups.  For instance, the following commands will backup everything from "dino"s home directory.  The next time you run this, only the changed files will get copied over.

rsync -avz /home/dino/      /media/backup/dino

---

