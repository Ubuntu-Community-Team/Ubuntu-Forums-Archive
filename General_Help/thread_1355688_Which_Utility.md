---
title: "Which Utility?"
date: 2009-12-15
forum: General Help
---

### Post by pluto4ps on 2009-12-15
I want to check HDD for bad sectors and any errors, so in windows we usually go for SCANDISK or CHKDSK.

I don't know in Ubuntu how to check HDD for bad sectors and any HDD issues?

---

### Post by TitanusEramius on 2009-12-15
[http://ubuntuforums.org/showthread.php?t=83223](http://ubuntuforums.org/showthread.php?t=83223)

For more reading on how to use fsck, type in "man fsck" in a terminal

---

### Post by audiomick on 2009-12-15
Hallo.
The command you want is "fsck" = file system check
look at the man page

```
man fsck
```

and this
[http://adminschoice.com/docs/fsck.htm](http://adminschoice.com/docs/fsck.htm)

---

### Post by wojox on 2009-12-15
System > Administration > Disk Utility

Click more information and run self-test.

---

### Post by ajgreeny on 2009-12-15
To force the system to run fsck at the next boot use the command ```
sudo touch /forcefsck
``` in terminal.  Next time you start the computer, the default system check that happens every 30 bootups will occur, and the count to 30 will start again.

I always do this if I have had a power failure that stopped my machine dead, without a proper shut-down, though so far I have never seen any system faults develop as a result of that.  The linux file system seems much more robust than ntfs or fat32.

---

