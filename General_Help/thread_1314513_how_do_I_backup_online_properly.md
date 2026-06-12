---
title: "how do I backup online properly?"
date: 2009-11-04
forum: General Help
---

### Post by bro on 2009-11-04
I have a huge question to which no doubt are multiple answers. 

How do I backup online properly?

Let me define what 'properly' means for me: 
- I have several GB in many (10-20)thousands of files.
- I want incremental backups
- I don't want to have to put everything in the same designated folder but pick several folders from /home (if symbolic links to/from these would work, that's okay)
- I want it to happen automatically or deadly simple and fast
- I want to be able to reach my files from other computers. 

What would be cool too:
- sharing files/folders publicly ones they are online.

What does it not mean? 
- Taking hours to do some kind of index of all my files and then slowly start uploading them. S3fox seems to do this. Though I have not finished the experiment with it. 
- Uploading all night every night. I like syncing to happen (almost) immediately when I change something.
- So far, it doesn't mean ubuntu-one, however sympathetic I am with ubuntu. 

I don't mind paying a little money. 
Should I use Jungledisk? Or Dropbox? Would this work smoothly with 20.000 files?

---

### Post by xuCGC002 on 2009-11-04
Ubuntu One is only $10 a month and provides all that and 50GB of space.

---

### Post by bro on 2009-11-04
Ubuntu one wants me to put everything in one folder. which is inconvenient. Also, it just didn't work when I tried it. after hours of indexing it hadn't uploaded anything but a part of the directory structure. I need something else.

---

### Post by FuturePilot on 2009-11-04
[Spideroak]("https://spideroak.com/") maybe?

---

### Post by rectagonal on 2009-11-04
I don't backup quite as much as you are asking for. But I use deja-dup (in the repositories) and have it back up to Amazon S3 .. That first backup takes forever, but the incremental backups after it are fine. Deja Dup encrypts the backups so privacy is assured. Be forewarned Amazon S3 charges of course...

---

### Post by bro on 2009-11-04
Is it possible to restore just a few files with Deja Dup or should I restore an entire backup?

---

### Post by nikgare on 2009-11-04
> Ubuntu one wants me to put everything in one folder
I should think you'll be able to use symbolic links.

---

### Post by rectagonal on 2009-11-04
> **bro said:**
> Is it possible to restore just a few files with Deja Dup or should I restore an entire backup?

You can't restore a single file from the gui. Deja Dup is a fancy front end for duplicty a command-line utility. I believe you could call the command-line utility to restore a single file.

Example found here : [http://wiki.kartbuilding.net/index.php/Duplicity_-_secure_incremental_backup#Restore_a_single_old_or_deleted_File_from_the_Encrypted_Backup](http://wiki.kartbuilding.net/index.php/Duplicity_-_secure_incremental_backup#Restore_a_single_old_or_deleted_File_from_the_Encrypted_Backup)

Although I have never done it. SO your mileage may very.

---

### Post by rectagonal on 2009-11-04
Oh never-mind answer is here : [https://answers.launchpad.net/deja-dup/+question/80570](https://answers.launchpad.net/deja-dup/+question/80570)

---

### Post by vashman on 2009-11-04
If your backing up really sensitive data then ubuntu one might not be the best choice right now (as it is still a beta [and i have had first hand problems with it.].)

The client though only syncs all the files to the computer, you can go to the web interface to get one file at a time.
Either way the client really seems lack luster right now, and you seem to have answered most of your own questions (use a different service if not just the program).

---

