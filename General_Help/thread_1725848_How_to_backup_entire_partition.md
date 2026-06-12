---
title: "How to backup entire partition"
date: 2011-04-10
forum: General Help
---

### Post by MrRichard on 2011-04-10
I've searched some older posts and they said to use partimage, but this program doesn't support ext4 file systems. Here's the original post: [http://ubuntuforums.org/showthread.php?t=845616](http://ubuntuforums.org/showthread.php?t=845616)
So how would someone backup their entire ext4 partition so the owner can mess around with some graphics drivers ;)

---

### Post by ~Plue on 2011-04-10
[clonezilla]("http://clonezilla.org/") or dd?

---

### Post by MrRichard on 2011-04-10
> **~Plue said:**
> [clonezilla]("http://clonezilla.org/") or dd?
It looks like clonezilla will do just fine, thank you for the quick response!

---

### Post by seawolf167 on 2011-04-11
I know the thread is already marked as solved, but if you are only changing settings in certain areas, you could also use rsync to copy the files to a different hard drive, then simply restore those particular files back to their original location if something goes wrong. 


Don't get me wrong - I ***love ***Clonezilla, but rsync will probably be faster as you don't need an entire hdd image for this. Manuals [here ]("https://help.ubuntu.com/community/rsync")and [here]("https://help.ubuntu.com/community/BackupYourSystem").

---

