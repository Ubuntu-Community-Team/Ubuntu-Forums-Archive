---
title: "Using FUSE to backup files on write?"
date: 2009-08-23
forum: General Help
---

### Post by WindPower on 2009-08-23
Hi, I've been looking at the hundreds of filesystems available for FUSE. What I'd want it to do is to monitor a directory for changes, and whenever a file changes in that directory, it gets copied to another location (a backup directory, probably remote but I can use FUSE to make the remote directory look like a local one, right? :))
However, I do NOT want the opposite to happen: when a file is changed in the backup directory, it does not get copied to the original directory.
Any tips/directions?

---

### Post by blueridgedog on 2009-08-23
Well, you could write an application that watched the directory and then copied files if a modification time was newer than a previously stored time, but I suggest a simpler approach.  Why not synchronize the directories, with the local being the master once every X minutes (you define X to suit you).

If I wanted to do it every 10 minutes say, I would put the following in my crontab file:

```
*/10 * * * * rsync -av /myfiles/ /Backup/myfiles --delete
```

(every 10 minutes of every hour, of every day of the month of every month on every weekday).

In the example, /myfiles/ is the path to your important directory, adjust as needed and /Backup/myfiles is where you want to put them.  

You can edit your crontab file with:

```
crontab -e
```

As with all code, get it working manually before you try and automate it.

---

