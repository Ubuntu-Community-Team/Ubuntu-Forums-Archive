---
title: "grsync manual/docs ?"
date: 2012-06-17
forum: General Help
---

### Post by thaitang on 2012-06-17
I have been using grsync for a couple of years with the most basic set-up (I guess). But I got the great idea to learn a few things and tweak my setup except I cannot find any manuals or docs for this app.

I am not interested in learning rsync from the command line, I am just wondering if there are even any decents tuts out there if no docs, cause I can't find em. I found some pages showing the basic settings I already have set but nothing that goes in depth.

any help appreciated for sure.
cheers,
tt

---

### Post by codemaniac on 2012-06-17
refer to the grsync section of the below page .

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by thaitang on 2012-08-03
> I am not interested in learning rsync from the command line
funny thing with lack of docs I ended up breezing over the rsync MAN and now I have a few regular b/u scripts setup for one-key backup. 

What was really kewl with grsync is setting up a b/u job and seeing the rsync command it creates and from there I just started reading about the options to fine tweak things the way I wanted.

Funny thing with gui's, I always think they gotta be easier, but not always the case.

---

### Post by Ralph L on 2012-08-03
I learned about rsync from the man page, but there is another gui for rsync that might interest you--LuckyBackup.  I have used it for a couple years and really like it.

---

### Post by kurt18947 on 2012-08-03
> **Ralph L said:**
> I learned about rsync from the man page, but there is another gui for rsync that might interest you--LuckyBackup.  I have used it for a couple years and really like it.

I just downloaded LuckyBackup.  I think you might be right, LuckyBackup might work better for me.  I didn't find a true sync function with Grsync.  I was able to back up folder A to folder B then back up Folder B to folder A.  This seemed to make both folders the same.   LuckyBackup looks like it might have a 'real' sync function though I haven't messed with it.   Nothing says you can only try one.  Try both and choose the one that works  best.

Update:  Yup, Luckybackup does indeed have a sync function.  I created two folders on an empty flash drive.  Put 1.txt, 3.txt, 5.txt in one folder. Put 2.txt., 4.txt, 6.txt in the second folder.  Started Luckybackup, selected 'synchronize' on a pull-down and clicked 'run'  Both folders contained all 6 files.  Rudimentary use but it could be useful for simple backups.

---

### Post by Ralph L on 2012-08-13
One limitation that I found in Luckybackup was that the snapshots (that go back in time) do not correctly preserve permissions, ACLs, and (I think) Extended Attributes.  The latest Backup has these things correctly, but when the folder/files get moved to the snapshot folder for an earlier date, they are lost.  I think this is because LuckyBackup doesn't set the "preserve all" parameter, when a copy (cp) or move (mv) command is executed.

Another limitation was that, with a set number of snapshots, the oldest snapshot gets deleted before the "pre-execution" commands (that the user can set) get executed.  In my case I wanted to have a message come up pre-execution that said "Is the backup disk drive plugged in?", with the option of dropping the task if it was not.  However, by the time the message came up, LuckyBackup had already deleted the oldest snapshot.  I got around this by running Luckybackup from a script, and using zenity to ask the question before calling Luckybackup.

---

