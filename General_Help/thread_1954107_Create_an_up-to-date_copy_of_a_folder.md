---
title: "Create an up-to-date copy of a folder"
date: 2012-04-07
forum: General Help
---

### Post by ZootHornRollo on 2012-04-07
Hi,

I have a folder on my hard drive with over 170GB of music ripped from my CD collection.

I would like to create a copy of this folder on my secondary drive in case of HD failure but i'd like it to automaticaly stay up to date if thats possible so that if i add new music it will get added to the back up copy.

any idea's on the best way to achieve this?

i had thought about using the back facilty provided with ubuntu but it seems to elect to keep all periodic back up copies until the HD is full before it starts to over-write - not what i want.

---

### Post by bobman321123 on 2012-04-07
Couldn't you write a shell script that copies that folder to the secondary drive and add the shell script to the system startup?

---

### Post by codemaniac on 2012-04-07
You can use a shell script as suggested by bobman321123 , but i wont prefer it to be called on each system startup .Instead you can schedule it from your crontab on daily basis .
You can also put find command useful while locating newer mp3 files and dumping into your secondary hdd .

---

### Post by Cheesemill on 2012-04-07
Create a script that uses rsync and put an entry for it in crontab.

I use this method to sync my music folder onto my backup drive once every hour (that's probably more often than necessary but I never know when or how long my computer is going to be on for).

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by NickellossAych on 2012-04-07
There are so many rsync options that seem so similar to me. Perhaps someone can help me out with my backups.  What I have now is 

```

    rsync -auvz SOURCE DESTINATION

```I'm using it to backup Documents, Music, Pictures and Videos, but I don't think it's doing exactly as I want.  I just changed the names of some music and ran the command, and in the destination folder there was the original copy and the new copy.  I know this is because of the -u, but what I am wondering is how to I make rsync only append changes to the current file, or overwrite if there are changes?

Any help would be greatly appreciated.

---

### Post by codemaniac on 2012-04-07
NickellossAych ou have just sucessfully hijacked the OPs thread .
Could you please start a new thread ?

---

### Post by Dave_L on 2012-04-07
> **NickellossAych said:**
> rsync -auvz SOURCE DESTINATION

I would use:

```
rsync -av --delete --stats SOURCE DESTINATION
```

Note that --delete will remove files in the destination that no longer exist in the source. You may or may not want that behavior.

--stats is helpful for seeing what's being done. It has no effect on the operation itself.

The -n or --dry-run option is also handy for testing. It shows you what would be performed, without actually doing anything:

```
rsync --dry-run -av --delete --stats SOURCE DESTINATION
```

> I just changed the names of some music and ran the command, and in the destination folder there was the original copy and the new copy.

That's sounds correct. Since you didn't use the --delete option, the old files weren't removed.

---

### Post by na5h on 2012-04-07
I'm sure you can find a suitable piece of software in the Software Center that can do periodical/automatic backups.

Also, have you considered using [RAID]("http://en.wikipedia.org/wiki/RAID")?

---

