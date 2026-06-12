---
title: "Please explain to the Newbie: Backups!"
date: 2009-12-22
forum: General Help
---

### Post by bostonjoe311 on 2009-12-22
Alright, I have been looking for the right backup solution for awhile without much success.  I think the main problem is I don't understand what I must do to fully backup my system, WHILE ALSO allowing for easy restore in the event of disaster.  I have used Norton Ghost/Acronis and, I must admit, they were very user friendly.  The linux backup solutions seem very intimidating.

I have read about most of the popular backup solutions such as clonezilla, rsync, flyback, etc, but they all operate using different principles.  Mainly I am looking for something like Norton Ghost, so could someone please tell me which software closely matches my needs:

1) can backup mounted partitions (does not require live cd like clonezilla)
2) makes backup file(s) that are smaller than original (some sort of compression)
3) incremental backups (user schedule)
4) gui interface (I don't trust myself on the command line)
5) easy restore process (restore to my previous state w/o re-installing Ubuntu)

I think my lack of understanding lies in the restore process.  In the event of diaster, do I perform a restore like Norton Ghost?  In other words, boot using a restore disk, then plop all the backed up contents back onto the hard drive?   If it helps I have 3 partitions, ext3 (/, /home, /data).  Thanks in advance.  Ya'lls help is appreciated.

---

### Post by starcraft.man on 2009-12-22
In short, I got nothing that meets everything you say. You describe a mythical backup app, that unfortunately does not exist yet for FLOSS. I am frankly uncertain what exactly you want, I'll point you to my backup wiki where I discuss all this. Pick what suits you.

IMO, you done most important step, separate partitions for home and data. In event of trouble to root, ya can reinstall painlessly and configs and data saved.
[URL="https://help.ubuntu.com/community/BackupYourSystem"]
Link.[/URL]

See partimage, grsync and simplebackupsuite, the three gui apps I discuss.

---

### Post by houseworkshy on 2009-12-22
Aptoncd is in the repositories and very easy to use.  Not quite and entire ghost but along with the live cd can put you right back where you started even if you are offline.

---

### Post by laceration on 2009-12-22
Simple Backup meets your criterion. I can't attest to its restore capabilities, because luckily I have never had to.  Though none of the many backup techniques are very complicated, they are are for the most part command line oriented.  Simple Backup is not and is the easiest to use.

---

### Post by bostonjoe311 on 2009-12-28
Sorry I didn't get back to you guys sooner.  I left town for Christmas and didn't get a chance to reply.  Thanks for all the suggestions.  starcraft.man, your link to the backup tutorial was very informative, but it prompted a couple more questions.

The tutorial showed that I don't want partimage/clonezilla because they require a live CD.  So, like laceration said, I guess grsync or SimpleBackup are the most obvious.  Tutorial mentions that rsync is a folder synchro program, while SimpleBackup is archiving program.  Does this mean rsync stores full copies of the original file, and does it maintain file structure?

My most important questions are about the restore process.  In the event of catastrophic failure or say I get a new hard drive, I want to be up and running with previous settings and files (disregarding media files).  Tutorial talks about restoring w/ SimpleBackup.  Would I first have to install Ubuntu before using SimpleBackup?  If so, and I restore backed-up files, will they overwrite current files, thereby giving me my previous system and settings?  What about grsync? I couldn't find anything about its restore process.

Thanks again for ya'lls help.

---

### Post by akernan on 2009-12-28
Checkout lucky Backup, it's in the repository.  It ties your backup to a recovery.  I use it with.  I tried Simple Backup/Restore & didn't like it as well.  I use lucky to backup my home dirs to a remote drive.

---

### Post by ezsit on 2009-12-28
Look into this:
[http://geekconnection.org/remastersys/remastersystool.html](http://geekconnection.org/remastersys/remastersystool.html)

It will create backups or redistributable ISOs. Personally, I create a DIST mode backup of the system and backup the data in my /home folder separately. In the event of emergency, I can reinstall from the DIST mode backup and copy my data back afterwards. It works very well. You can create a true backup of your installed system and use the installer on the backup to reinstall your system.

---

### Post by bostonjoe311 on 2009-12-29
Hey akernan, after looking at the videos of lucky backup it does look interesting.  When you perform a backup, it's 1-for-1 right?  Also, what exactly does it mean when they tie a recovery to the backup?  I couldn't find a decent explanation of the recovery task, so I was wondering if you had used it.

---

### Post by akernan on 2009-12-29
Yea, I used the recovery. Unfortunately. :-D

You just configure the backup and the recovery is configured for you, automagically.  You can also configure the recovery yourself.

I'm not sure what you mean 1-for1.

---

