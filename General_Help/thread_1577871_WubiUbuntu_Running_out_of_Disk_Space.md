---
title: "Wubi/Ubuntu Running out of Disk Space"
date: 2010-09-19
forum: General Help
---

### Post by beadevilg on 2010-09-19
My wubi-installed Ubuntu is telling me that I'm running out of disk space.  At first, it would not login, telling me that the GNOME Power Manger was not properly installed; however, that turned out to be a disk space issue.

I deleted a bunch of files from Downloads, and the system logged in fine.

Now, in analyzing the disc usage, I seem to have a couple problems:

1. It is telling me that my root directory is full (120GB used, 108GB available, but still shows 100% usage).
2. It shows that my /host is near 100%.

Any ideas on what might be eating up my disk space?

Thanks.

---

### Post by bcbc on 2010-09-19
Most likely you are running out of room on your root.disk (the virtual disk that wubi uses is actually a file). It is unrelated to the amount of space on the partition that it resides - and is set when you installed the first time.

run the following from a terminal 
```
df -h
```

the first line /dev/loop0 will show you the space available on the root.disk and it's original size (first column).
At the bottom a line like /dev/sda# will show you the space available on the partition (/host) you installed wubi on.

You can copy some of your data out of /home (i.e. out of the virtual disk) to the /host to make room, or you can try creating a new virtual disk for /home (the wubi guide has a script). If you haven't been using it much it might just be easier to backup data, and reinstall with a larger virtual disk.

---

### Post by beadevilg on 2010-09-25
Thank you, BCBC.  That did work at first.  Now, I'm getting the same message again with dev/loop0 being completely full (17G).

Here is my df -h:

/dev/loop0, 17G of 17G used (100%) mounted on /
/dev/sda1 120G of 223G used (54%) mounted on /host
/dev/loop1 [the new one I created] 2G of 14G used (17%) on /home

The root is still filled up.

---

### Post by bcbc on 2010-09-25
I assume you deleted the backup (/home.backup) after you migrated it to the new disk? (assuming you've verified everything is working correctly).

It's strange that you're using 17GB of data for / - and in your new /home you're only using 2GB of data. That means that even if you didn't delete the /home.backup you still have 15GB of other data. Which is a lot.

Try running "gksu baobab /"  (the disk usage analyzer) and try and identify where that stuff is. Perhaps you have an out of control log file in /var/log

---

### Post by beadevilg on 2010-09-26
Thanks again, BCBC.

I think I found the problem: Simple Backup (SBackup).  It was created gigantic files every week on my disk, which ate it all up.  I deleted the files and used Synaptic Package Manager to remove SBackup.

I'll also check for the /var/log files to see what might be in there.

Great solution!  Thanks for your help.

---

