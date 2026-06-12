---
title: "Needs proof-reading of rsync param -"
date: 2012-05-09
forum: General Help
---

### Post by AlexOnVinyl on 2012-05-09
Currently using rsync to backup my Home directory.  I had previously used this param to exclude anything that began with "." - folders and files, but realized, I could be losing some important files with that.

Here was the original command with param:

```
rsync -r -t -v --progress -b -s --exclude .* /home/alex/ /media/Recov/alex/
```

Then I tweaked it to only apply to directories that began with "."

```
rsync -r -t -v --progress -b -s --exclude .*/ /home/alex/ /media/Recov/alex/
```

Does can someone proof read this for me and let me know if I'm on the right track?

btw - this part: ```
/home/alex/ /media/Recov/alex/
``` is just me backing up my home folder to a partition on my external drive called "Recov" - dont mind it - its just merely the destination.

---

### Post by mendhak on 2012-05-09
You can test out your new command by adding --dry-run or -n to it, which will tell you what it would have done but wont' actually do it.  You've already got -v verbose, so that should be good enough.

---

### Post by Dennis N on 2012-05-09
If you want, you can combine single letter options for brevity:

rsync -rtvbs

if the destination is a FAT16 or FAT32 file system, add --modify-window=1 to the options. the man page explains why.

source and destination look ok.

FYI: for comparison, I use rsync -rti for the basic options. option 'i' gives a list of all files changed or added to the destination. If you don't want old deleted files to accumulate in the destination, add --delete.

Added:

Not sure what the -b is going to produce. Backup files of the backup files? Where do they go?

---

### Post by surfer on 2012-05-09
you can even do incremental backups: assuming you have already backed up /src to /bkp/date0, you can do an incremental backup to /bkp/date1 with
```
/usr/bin/rsync --link-dest /bkp/date0 ...
```
where ... are your rsync opts from above.

i then usually make a link
```

$ ln -s /bkp/date1 /bkp/current

```
or something alike. my script then knows it has to use /bkp/current as link-dest.

---

### Post by AlexOnVinyl on 2012-05-09
> **Dennis N said:**
> If you want, you can combine single letter options for brevity:

rsync -rtvbs

if the destination is a FAT16 or FAT32 file system, add --modify-window=1 to the options. the man page explains why.

source and destination look ok.

FYI: for comparison, I use rsync -rti for the basic options. option 'i' gives a list of all files changed or added to the destination. If you don't want old deleted files to accumulate in the destination, add --delete.

Added:

Not sure what the -b is going to produce. Backup files of the backup files? Where do they go?

-b backing up my Home Folder to make backup files of the current ones.

> **surfer said:**
> you can even do incremental backups: assuming you have already backed up /src to /bkp/date0, you can do an incremental backup to /bkp/date1 with
```
/usr/bin/rsync --link-dest /bkp/date0 ...
```
where ... are your rsync opts from above.

i then usually make a link
```

$ ln -s /bkp/date1 /bkp/current

```
or something alike. my script then knows it has to use /bkp/current as link-dest.

Thanks guys, All setup to work.

---

