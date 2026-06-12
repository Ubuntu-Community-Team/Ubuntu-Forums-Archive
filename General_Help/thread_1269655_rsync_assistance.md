---
title: "rsync assistance"
date: 2009-09-18
forum: General Help
---

### Post by SteveMosher on 2009-09-18
Ok here we go.
 
I have mounted remote drives and I am trying to get rsync to just sync certain directories within these mounted folders.
 
Example:
/mnt/bkmasterbackup1
/mnt/bkmasterbackup2
/mnt/bkmediabackup1
/mnt/prodnas02
/mnt/prodnas03
/mnt/prodnas04
/mnt/prodnas05
 
Inside these mounted drives I have a folder called DR
Example:
user(at)machine# pwd
/mnt/prodnas02/ArdentHS/DR
Im trying to just sync /mnt/prodnas02/*/DR/*
What Im trying to use is ..
rsync -rhu --progress --include-from=/root/rsync-include/drfolders --log-file=/var/log/copy.log /mnt/prodnas02 /mnt/backup01/
within my drfolders file I have something like 
/*/*/DR/*
I've tried several different lines and include or exclude lines but for some reason I am truley missing something.
Any assistance with the syntax would be great. 
Thanks in advance.

---

### Post by sedawk on 2009-09-18
First please use the "-n" and "-v" option so you can test
rsync with verbose output without really doing anything!

After shortly browing through the PATTERN section of
the rsync man pages I would assume you should
try again replacing your pattern "/*/*/DR/*"
with "/*/DR/*" or "*/DR/*".

What you can try is to build a solution on an external loop.
Here some starting point:
```

find /mnt/prodnas02 -type d -name DR -print |while read BKUP;do
  echo "If needed: mkdir -p" \"/mnt/backup01/$BKUP\" 
  rsync -ruvn \"/mnt/prodnas02/$BKUP\" \"/mnt/backup01/$BKUP\"
done

```

---

### Post by SteveMosher on 2009-09-18
I did at elast try and read the man pages but I got really lost in there with the from-include file lines.
 
I did try the "*/DR/*" and that turned out to be a downer.  However I didnt try "/*/DR/*" this may be my issue.  I will test this now.
 
As for the bash snipplet I cant thank you enough.  That very well may be a better choice.
 
I will keep you informed of what I find.

---

### Post by SteveMosher on 2009-09-18
as for the snipp I get this ...
 
 
sending incremental file list
rsync: change_dir "/root/"/mnt/prodnas02//mnt/prodnas02/Richardson" failed: No such file or directory (2)
rsync: change_dir#3 "/root/"/mnt/backup01//mnt/prodnas02/Richardson" failed: No such file or directory (2)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(632) [receiver=3.0.5]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]
If needed: mkdir -p "/mnt/backup01//mnt/prodnas02/Parma/DR"
 
Maybe spacing

---

### Post by SteveMosher on 2009-09-18
damn it.  This didnt work out.  "/*/DR/*"

---

### Post by pandanuma on 2009-09-18
> **SteveMosher said:**
> damn it.  This didnt work out.  "/*/DR/*"

try dropping the asterisk at the end
or try dropping the /* at the end

this is how I copy all files and directories on my desktop to an external harddrive:

rsync -av /home/desktop /media/TREKSTOR/rsyncbu

my only problem is trying to update the backup with only new files and directories...
rsync **-avu** /home/desktop /media/TREKSTOR/rsyncbu still takes over an hour to backup and seems to be a complete new backup

---

### Post by SteveMosher on 2009-09-21
> **pandanuma said:**
> try dropping the asterisk at the end
or try dropping the /* at the end
 
this is how I copy all files and directories on my desktop to an external harddrive:
 
rsync -av /home/desktop /media/TREKSTOR/rsyncbu
 
my only problem is trying to update the backup with only new files and directories...
rsync **-avu** /home/desktop /media/TREKSTOR/rsyncbu still takes over an hour to backup and seems to be a complete new backup
 
 
I tried that dropping of the trailing * but no go.  We used the -a flag here and it also took a VERY VERY long time to 'do stuff'.

---

