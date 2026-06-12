---
title: "rsync for initial backup then maintenance backups"
date: 2011-05-09
forum: General Help
---

### Post by eenu on 2011-05-09
Hi,

So I am using rsync (3.0.7 on MAC OSX) to backup one hard drive to a folder on another one. The is USB drive to USB drive and I have done the initial backup from one drive to a new formatted other drive with the following command:

```
rsync -avX --progress /Volumes/Source /Volumes/Destination
```

This all appears to be going smoothly as I type. I am going to write a script to do subsequent backups in the future. What I was to do is make the destination an exact copy of the source. I want to only update things that have changed and to delete files and directories that I have deleted at source and obviously add new ones to the destination that I created since last backup. The code i was proposing was:

```
rsync -avX --progress --delete /Volumes/Source /Volumes/Destination
```

I have a couple questions regarding this. Does "--delete" delete directories as well as files? From what I have read I would say it doesn't, however, I don't see a command to do otherwise except maybe "--prune-empty-dirs". I am not sure I fully understand that command. Can anyone help here?

Secondly, "--ignore-existing" do I require this to avoid rsync rewriting everything again?

---

### Post by SecretCode on 2011-05-09
Not sure about deleting directories that don't exist in the source. I think --delete does do this, but you could easily run a small test!

Incremental backups is what rsync is good at. It will not re-send files that exist on the destination and haven't changed - unless you force it to (I haven't done that but I think there is an option for it).

In other words, normally you can use exactly the same command for the initial backup (including --delete though it won't do anything) as for subsequent incremental backups.

---

### Post by eenu on 2011-05-09
> **SecretCode said:**
> Not sure about deleting directories that don't exist in the source. I think --delete does do this, but you could easily run a small test!


I ran a test and it would appear that it does delete empty folders as well as getting rid of files :D

---

