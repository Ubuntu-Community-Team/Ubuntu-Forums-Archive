---
title: "cannot access rsync'd folder on remote side"
date: 2010-06-24
forum: General Help
---

### Post by jones.79 on 2010-06-24
[FONT=-moz-fixed]Hello! 

I found a strange problem while using rsync to backup my files. 

I use a script: 

------------------ 
#!/bin/bash 

SOURCEDIR="/" 
TARGETDIR="root@DLINK-13F017:*/mnt/HD_a2/administrator/RAIDBackup/*" 
LOGFILE="--log-file=*/home/administrator/*.rsync/rsync_dns323.log" 
OPTIONS="-avz -e ssh --stats --progress --delete --delete-excluded" 
EXCLUDES="--exclude-from=*/home/administrator/*.rsync/exclude_dns323.txt" 

sudo rsync $OPTIONS $LOGFILE $EXCLUDES $SOURCEDIR $TARGETDIR 2>  */home/administrator/*.rsync/errorlog_dns323.txt 
-------------- 

Exclude-From contains: 

- */dev/* 
- */sys/* 
- */proc/* 
- */home/administrator/*.gvfs/ 
- */home/administrator/*.rsync/rsync_dns323.log 
- */home/administrator/temp/NAS/* 

------------ 

Well, everything is copied as expected I guess, except ~*/Desktop/*. 
The directory on the target side -  the file manager says there is no  content. 

I even cannot access it via console using su or sudo, I get permission  denied. 

This has surely something to do with the rights, but I don´t get the clue. 

~*/desktop/*-folder source-side: 
750 drwxr-x--- administrator root 

~*/desktop/*-folder target-side: 
750 drwxr-x--- administrator administrator 

I hope you can help me! 

Thanks!
jones



[/FONT]

---

### Post by CharlesA on 2010-06-24
Use the -a switch with rsync. That will preserve permissions/owners/link/etc.

```
-a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
 -r, --recursive             recurse into directories
 -l, --links                 copy symlinks as symlinks
 -p, --perms                 preserve permissions
 -t, --times                 preserve modification times
 -g, --group                 preserve group
 -o, --owner                 preserve owner (super-user only)
 -D                          same as --devices --specials
```

---

### Post by jones.79 on 2010-06-24
Hi!

I am using the -a switch...thats why I am so confused...

> OPTIONS="-avz -e ssh --stats --progress --delete --delete-excluded" 

The files seem to be there as I watch the console output and they are listed as "uptodate", I just cannot see them and have no clue why...

---

### Post by CharlesA on 2010-06-24
Strange. Try adding the -i switch instead of the -v switch, that'll show if it's changing any permissions.

---

### Post by jones.79 on 2010-06-24
I figured out that it had something to do with user permissions.

Backup was done via SSH, the filesystem in Nautilus was mounted via SMB, but 
using a different user than the backup was done with. 
And due to the rights set to 750 as I mentioned above others hat no permissions and could not see files in ~/Desktop. 

Thanks for the help!!

jones

---

