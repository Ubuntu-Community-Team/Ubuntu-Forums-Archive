---
title: "live mirroring local directories"
date: 2012-02-03
forum: General Help
---

### Post by M!K3_$ on 2012-02-03
Hello,

Here is the scenario. 
I want to create a live mirror of my home directory so that everytime something happens in home it also happens in another directory. I have another hard drive mounted and I want it to mirror /home/user/.

IF I can't do this, I was thinking differential backups would be acceptable.

Thank you!

---

### Post by Vishnu V on 2012-02-03
Hi,
What about using RAID level 1 ?

---

### Post by M!K3_$ on 2012-02-03
> **Vishnu V said:**
> Hi,
What about using RAID level 1 ?

I just want to mirror one directory. If I lose the OS, it isn't a big deal. I just reinstall it.

---

### Post by yetiman64 on 2012-02-04
To do it at a folder level (not using RAID volumes) I can think of 2 possibilities for you to look into.

_**1st **_(**note this method is potentially dangerous to data if used incorrectly**), bind mounting. 

The home folder is bind mounted to the backup folder at startup with an entry added to /etc/fstab. It is potentially dangerous to your data if you remove a file/folder from the backup without first unmounting the home folder from the backup folder, the same file/folder in your home directory is also removed/altered. [I][U]Take extreme care if you go with a method like this, do a lot of research on this first.
[/U][/I] [U][B]
or 2nd[/B][/U] (preferred method for data safety). Use rsync or grsync to mirror your home folder to a backup folder. I have never used this myself, but from my reading of posts on this forum I believe it is possible to do. [[COLOR=Blue]--info link for rsync / grsync--[/COLOR]]("https://help.ubuntu.com/community/rsync")

Best of luck with this, yetiman64

---

### Post by Lars Noodén on 2012-02-04
You can use [rsync](http://manpages.ubuntu.com/manpages/oneiric/en/man1/rsync.1.html) to keep the directories in sync.  Then you could use [incron](http://manpages.ubuntu.com/manpages/oneiric/man5/incrontab.5.html) to run rsync when something changes in that directory.  That might be close to what you are trying to do.

---

