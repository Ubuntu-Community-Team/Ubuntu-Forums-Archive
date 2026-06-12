---
title: "Looking for Simple Backup Commandline Program"
date: 2009-07-23
forum: General Help
---

### Post by zzzBrett on 2009-07-23
I have two hard drives that store user files.  Every night, I would like to execute a command (no gui), that basically duplicates both of these hard drives.

I'm switching over from a windows computer that does this, and I had a program that did this and compared the files and only synced the changed files.

The few that I have used attempted to create a logarithmic backup of some sort, or wanted to compress in a tar - I just want the files to be transferred without compression, exactly how they are on the original hard drive.

Any suggestions?

---

### Post by bacil on 2009-07-23
easy it can be scripted :-)

do you want filebased backup  or block based ?

is target big enough for both ?

---

### Post by Cheesemill on 2009-07-23
rsync will do everything you need.

---

### Post by zzzBrett on 2009-07-23
> **bacil said:**
> easy it can be scripted :-)

do you want filebased backup  or block based ?

is target big enough for both ?

I don't know what block based backup is, so I assume I want file based.  And the target hard drive is the same size as first hdd, so it should have enough space.

---

### Post by zzzBrett on 2009-07-23
> **Cheesemill said:**
> rsync will do everything you need.

I've tried rsync, but I couldn't get it working correctly.  This is the command I was using:

```
rsync -r -n -t -v --progress -c /media/HDD1/ /media/HDD2/
```


Is there something wrong with this?

---

### Post by XCan on 2009-07-23
> **zzzBrett said:**
> I've tried rsync, but I couldn't get it working correctly.  This is the command I was using:

```
rsync -r -n -t -v --progress -c /media/HDD1/ /media/HDD2/
```


Is there something wrong with this?

What was the issue that you were having? I take it that you know that your command won't do anything live since -n specifies dry-run. In either case, I would use 
```
rsync -av --progress /media/HDD1/ /media/HDD2/
```
since you were interested in duplicating the drives. -a flag will preserve timestamps ownerships etc.

---

### Post by zzzBrett on 2009-07-23
:) I believe the -n was the problem -- I used a GUI to setup the command, then copied and pasted (lazy).  I will try this out.  Thanks!

---

