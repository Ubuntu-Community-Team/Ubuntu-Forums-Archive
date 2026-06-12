---
title: "Backups - what should I exclude?"
date: 2010-09-08
forum: General Help
---

### Post by 2CV67 on 2010-09-08
I regularly back up my home directory to an external hard drive, using Grsync.
So I regularly watch it reeling off what it is backing up & am surprised at the time it spends on stuff like:
- nautilus
- cache
- thumbnails
- etc etc

I can imagine that these space-consuming & time-consuming copies might not actually have much, if any, value.

I am just about ready to chop Nautilus & Cache, but doubtful about Thumbnails.

What are your views on the value of these items in a backup?
What else should I leave out, which takes a lot of time & space but has little or no value?

Thanks for all suggestions!

---

### Post by TwelveGauge on 2010-09-08
Well...what are you most interested in saving in the event of total system death?

If you don't mind having to reinstall your OS (if your system goes) but want your other files to survive, why not just back up your home directory? and/or whatever other useful files you have stored around --conky scripts, various interesting shell scripts, etc.

---

### Post by ubulal on 2010-09-08
Thumbnails and cache are only there for speeding up repeated uses of the same data.  They will be regenerated after restore, so can safely be excluded from backups.  Don't forget to exclude ~/.local/share/Trash.

---

### Post by oldfred on 2010-09-08
I copied this from another poster (forgot who to give credit to). But this is pretty much what I do. Except I only copy those files I know I have changed in /etc and plan on a new system install if I have a total crash.

I backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script I wrote to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup

Installed applications list (to make it easy to reinstall everything)
dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by 2CV67 on 2010-09-13
This post transfered to new thread.

---

