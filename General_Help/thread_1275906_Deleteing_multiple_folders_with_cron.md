---
title: "Deleteing multiple folders with cron"
date: 2009-09-26
forum: General Help
---

### Post by TOUR on 2009-09-26
Hello,

I would like to use a cron job (unless there is a better solution) to delete multiple folders in multiple directories older than a certain date.

For a quick background, I have small video clips uploaded to my computer on a daily basis.  Any files older than two weeks I need to remove manually.  When I'm on vacation or away for a little bit I end up loosing some work due to the inability to remove files manually.

Here is an example of the folder hierarchy.
/data/alpha
/data/alpha/gamma/monday
/data/alpha/gamma/tuesday
/data/alpha/gamma/wednesday
/data/alpha/omega/monday
/data/alpha/omega/tuesday
/data/alpha/omega/wednesday

So /data is a shared folder that all of my other folders are in.  I want the ability to remove the "gamma" folder if the date of the folder is older than 21 days (but leave the omega folder alone until its time has come).  This includes all sub directories and video files.

I found the code to do this on an individual file basis, but not for a folder.  

Hopefully y'all can help me out.  Would be greatly appreciated!

---

### Post by DaithiF on 2009-09-26
using the find command, something like...
```
find /data/alpha -maxdepth 1 -type d -mtime +14 -exec rm -rf {} \;
```

so for any directories 1 level below  /data/alpha, which were last modified more than 14 days ago, delete them and their subdirs.

when running this first, change the rm -rf piece to echo to make sure you are seeing the directories you expect -- once you're happy its finding the right ones then use rm -rf to delete them.

you can either add this to crontab as a single command, or you can put this into a script and call the script from cron.

---

### Post by TOUR on 2009-09-26
> **DaithiF said:**
> using the find command, something like...
```
find /data/alpha -maxdepth 1 -type d -mtime +14 -exec rm -rf {} \;
```

so for any directories 1 level below  /data/alpha, which were last modified more than 14 days ago, delete them and their subdirs.

when running this first, change the rm -rf piece to echo to make sure you are seeing the directories you expect -- once you're happy its finding the right ones then use rm -rf to delete them.

you can either add this to crontab as a single command, or you can put this into a script and call the script from cron.

Thank you, I will set this up in my test environment.  I was not expecting the resolution to be this easy after spending so much time researching it this morning.

---

