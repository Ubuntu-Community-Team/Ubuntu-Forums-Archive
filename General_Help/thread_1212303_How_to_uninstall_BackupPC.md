---
title: "How to uninstall BackupPC ??"
date: 2009-07-13
forum: General Help
---

### Post by mirkko22 on 2009-07-13
Hello

I have install BackupPC under Ubuntu 9.04 and am not able to use it and I would like unninstall all files/stuff related to this software...

In fact am newbie with command line this kind of software are to much complexe for me......and it seem to be not installed properly...is just a mess..

I get some problem because now I get a full backup of my files everyday and my hard disk is full...I don't know how to disable this...

Anyone can help me please ??

thanks for your time...

---

### Post by ajgreeny on 2009-07-13
How did you install it in the first place?

---

### Post by mirkko22 on 2009-07-13
That the problem...I don't know exactly...I don't have install it properly...I have download the package from the website and I have start to run the file configure.pl in command line...After that I have do some kind of config and stop all by closing the terminal...

In fact when I make a search on my system for BackupPC file I don't find nothing special...All files present in the package are founded inside Trash folder (where I have put it) but no in other place...

I can find a folder called "Backup" inside var folder and some other folder like "spool" and "cups"...If am not wrong all this folder are related to BAckupPC software... Yesterday I have simply delete the folder backups and no more....and today I see this folder are again present...that mean the software continue to make backup...

Any suggestions ??

---

### Post by cariboo on 2009-07-14
> I can find a folder called "Backup" inside var folder and some other folder like "spool" and "cups"...If am not wrong all this folder are related to BAckupPC software... Yesterday I have simply delete the folder backups and no more....and today I see this folder are again present...that mean the software continue to make backup...

The directories, /var/backup, /var/spool and /var/cups are sytem directories nad have nothing to do with backuppc. I you delete them, you will run into problems.

If the only backuppc files you can find are in your trash, then you probably never installed it.

BTW this is in the wrong section, I'm moving it to General Help

---

### Post by mirkko22 on 2009-07-14
In fact I have just delete (as root) /var/backup because I have see it is a new folder (create the same day of my BackupPC testing) and inside I have see 2 big backup.... I have another folder but called /var/backups ... After 1 days the folder "backup" come back alone.... strange no ??

---

### Post by ajgreeny on 2009-07-16
It sounds as if BackupPC is like sbackup, and puts the backup file in /var by default.  This seems a slightly silly place to me for a bacup default location, though I suppose it is better than having no backup at all.  What's the use of a backup to people if the actual backed up file(s) is on the machine that has a major problem?

I know this does not really answer your question, but just thought I would add this as a general comment.

---

