---
title: "Best backup before update"
date: 2012-10-04
forum: General Help
---

### Post by gardengxc on 2012-10-04
I'm looking to update from Ubuntu 11.10 to 12.10 in a few days but I want to be able to go back to 11.10 in case of the new version kills my install or not working with my games or you know sucking.

Now I have enough room on my 2nd hard drive to do a full backup uncompressed. I was thinking about just copying the partition but I don't want to fuss with fixing it afterwards. 

So is there a simple program that can backup the whole hard drive and restore it without needing to log in? (in case 12.10 doesn't even turn over.)

---

### Post by apochry on 2012-10-04
In this [wiki]("https://help.ubuntu.com/community/BackupYourSystem") you can find a list of Backup Utilities. I've never used any of them, thought.
I usually do the second thing you've mentioned - copying the partition and running [boot-repair ]("https://help.ubuntu.com/community/Boot-Repair")after I restore it. Not saying that it is the best, or even good, solution. It's just simple.

Good luck with that!

 - Christo

---

### Post by Stonecold1995 on 2012-10-04
You can use rsync.  It allows incremental backups, so you won't have to delete your old backups, you just update them.  If you don't want to use command-line, you can install a GUI frontend for rsync called grsync, which can makes it easier to use.

```
sudo apt-get install grsync
```

EDIT: Sorry I misread your post.  I suppose you could use rsync without logging in, by booting into recovery mode...

---

### Post by jerrrys on 2012-10-04
Maybe [Clonezilla]("http://clonezilla.org/")

---

