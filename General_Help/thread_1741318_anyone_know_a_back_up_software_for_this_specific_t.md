---
title: "anyone know a back up software for this specific task?"
date: 2011-04-28
forum: General Help
---

### Post by fuzzylogic25 on 2011-04-28
Hi,

I have moved from Windows XP a while back, and i must say I love ubuntu. But finding problems that had the flexibility in windows has been difficult. One is the back up software SyncBackPro which I used in Windows.

Basically, I had this set up:

1. keep a mirror of contents in directory (eg /home/user/uni). Run this every 5minutes.

2. Keep a back up with versioning of directory (eg /home/user/uni). Run this every 5minutes.

For the 2nd point, it means if we had file /home/user/uni/notes.txt and it was backed up today at 8pm, then we modified it at 8:02pm...then what happens is at 8:05 it will create a version of that new modification. so typically u would see this in the back up destination:
-/home/user/uni/notes.txt - the latest version
-/home/user/uni/$VER/notes_0800_27MAR_2011.txt

So the second one is the previous version. and it could maintain like a thousand different versions of this!

What program best provides something like this?

---

### Post by HermanAB on 2011-04-28
Howdy,

Read up on rsync and dejadup using [http://google.com/linux](http://google.com/linux)

---

### Post by fuzzylogic25 on 2011-04-28
thanks, i checked out deja-dup but it doesnt offer hourly back ups. it is not flexible enough. but i think i should just look into rsync and cron.

---

### Post by HermanAB on 2011-04-28
Exactly, make a one line rsync script and drop it into /etc/cron.hourly then make it executable.

---

### Post by fuzzylogic25 on 2011-04-28
That is true. But what about versioning? Thats a very important feature to me. Where it basically keeps versions of a file if modified.

Eg, if file cat.txt is backed up at 9pm then at 9:30pm if it is modified at the source, we will have a new version for cat.txt and the old version would be named cat_9pm_29april.txt or something.

can rsync do this>

---

### Post by tredegar on 2011-04-28
> can rsync do this>
Not the best tool.

You could write some custom script, or look at [backintime]("http://freshmeat.net/projects/backintime") (it's in the repositories).

---

### Post by SecretCode on 2011-04-28
rsync can do this with the --backup and --suffix options

```
rsync /path/from /path/to/backups --backup --suffix=_`date +%Y%m%d-%H%M%S` -Pitr
```

---

### Post by tredegar on 2011-04-28
> rsync can do this with the --backup and --suffix options
I just learnt something. Thanks.

---

### Post by fuzzylogic25 on 2011-04-28
Thank you for all the help. It looks like rsync is certainly something I must look into properly.

One more thing, my old windows back up tool had this option where it never actually searched the destination files/folders when comparing with the source, since the destination doesnt change in some situations. So instead, it maintained a list of all files/folders in destination and compared the source with that. The list always got updated of course. This way, only one hard disk has to go through all the checks, the source.

Can Rsync do this at all?

---

### Post by oldfred on 2011-04-29
Links to a couple to examples of rsync.

This is the one I have used. But of course I changed to my paths.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)

things to backup
Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

You can review the man page, but for rsync it has  too many options. Best to review samples.

man rsync

Linux has multiple timestamps.
[http://linuxboxadmin.com/micro/micro-howtos/system-administration/file-timestamps.html](http://linuxboxadmin.com/micro/micro-howtos/system-administration/file-timestamps.html)

---

### Post by SecretCode on 2011-04-29
> **fuzzylogic25 said:**
> One more thing, my old windows back up tool had this option where it never actually searched the destination files/folders when comparing with the source, since the destination doesnt change in some situations. So instead, it maintained a list of all files/folders in destination and compared the source with that. The list always got updated of course. This way, only one hard disk has to go through all the checks, the source.

Can Rsync do this at all?

I'm pretty sure it can't and won't ... it's designed as a remote sync tool where scanning the directories on each end is 'cheap' compared to sending stuff across the wires. It does not have a repository of what files exist elsewhere and what has been backed up. It's **good** at doing backups but it doesn't do everything you might want from a backup tool.

---

