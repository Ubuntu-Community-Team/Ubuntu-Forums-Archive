---
title: "Real-time Backup Solution"
date: 2010-03-23
forum: General Help
---

### Post by gdi2k on 2010-03-23
Greetings, 

I'm looking for a backup solution that I can just set and forget. Something like Dropbox or UbuntuOne, but for backing up to a local or network attached drive, rather than the web. 

Specifically it should: 
[LIST]
[*]Detect changes to files and directories and backup changes immediately.
[*]Store multiple revisions.
[*]Not be a complete resource hog.
[/LIST]

I've tried Back in Time and Flyback - neither support monitoring for file changes, and both take forever to run and usually don't complete. 

I know Apple has Time Machine which does a great job. I also have a WD Passport which came with free Windows software which does just fine too. But I can't find anything like it for Linux. 

Suggestions?

---

### Post by moldy on 2010-04-16
I too would be very interested in something like this...

---

### Post by Serpher on 2010-04-16
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

You might also want to look into the "dd" command. There doesn't appear to be a GUI application for this, but there are programs you can run in the terminal to do this.

Eg,

Backup:
```
$dd if=/dev/sda1 of=/media/<externalhardrive>/backup.img
$gzip /media/<externalhardrive>/backup.img
```

Restore:
```
$gunzip /media/<externalhardrive>/backup.img.gz
$dd if=/media/<externalhardrive>/backup.img of=/dev/sda1
```


If you wipe the partition off, you'll have to make it again using fdisk or the disk manager if you're more comfortable with a GUI.

---

### Post by switch10 on 2010-04-16
I use rsync in a cron job.  

If you are looking for a GUI, check out "back in time".  Its a time machine clone I think...

[http://backintime.le-web.org/](http://backintime.le-web.org/)

```
 sudo apt-get install backintime-common
```

---

### Post by mk1w86 on 2010-04-16
You could have a look at rsnapshot which uses rsync:

[http://rsnapshot.org/](http://rsnapshot.org/)

---

### Post by iponeverything on 2010-04-16
> **gdi2k said:**
> Greetings, 

I'm looking for a backup solution that I can just set and forget. Something like Dropbox or UbuntuOne, but for backing up to a local or network attached drive, rather than the web. 

Specifically it should: 
[LIST]
[*]Detect changes to files and directories and backup changes immediately.
[*]Store multiple revisions.
[*]Not be a complete resource hog.
[/LIST]

I've tried Back in Time and Flyback - neither support monitoring for file changes, and both take forever to run and usually don't complete. 

I know Apple has Time Machine which does a great job. I also have a WD Passport which came with free Windows software which does just fine too. But I can't find anything like it for Linux. 

Suggestions?

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

It supports mirroring and snapshots.

---

