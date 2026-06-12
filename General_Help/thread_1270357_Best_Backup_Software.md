---
title: "Best Backup Software"
date: 2009-09-19
forum: General Help
---

### Post by Maintech on 2009-09-19
This question is for the Gurus. Ubuntu comes with a variety of backup software. I have no wish to try them all. The backups will be from several home computers to a central home server. I want to be able to back up /home directory so that after a fresh install I can "restore" the backup to the newer version Ubuntu just installed. This will be in case an "upgrade" doesn't work. 9.04 comes with one installed but have never worked with it. Please include links to any documentation of use with any software recommended.

Thank you all for your help....this time and in the past.

---

### Post by x C0MMAND0 x on 2009-09-19
I use rsync.  It is an excellent program that is very simple to use.  If you prefer a graphical interface, check out grsync.  Be sure to back up you home folder, but also your /etc/ folder, as that is where a lot of important information lies.

Additionally, check out a program called ApTonCd (system>administration>you_might_have_it_here).

This will back up every single program that you have to a .iso  You can then use the program on a new computer to restore the .iso and install all of your applications again.  Please keep in mind this is 32bit / 64bit specific.  Example: you can't create a backup of all your programs on a 64bit system and try to restore them on a 32bit system.

That is just my $0.02, I'm sure everyone will have their own method of backing up.

---

### Post by Maintech on 2009-09-19
> I use rsync. It is an excellent program that is very simple to use. If you prefer a graphical interface, check out grsync. Be sure to back up you home folder, but also your /etc/ folder, as that is where a lot of important information lies.

Thanks for the quick reply. My main purpose of a backup is to keep all my pictures, videos, and documents. Also, many scripts I have written. I am hoping to backup to archive that I can do incremental backups to. My wife also needs to be able to do the same. It needs to be a compressed archive because we both have a lot to back up and the server doesn't have several terabyte to use for storage. And to complicate matters, I have other computers that, although they contain less (mainly scripts), I need to keep a running backup of them also. This is less for repair of an existing OS than it is a way to "restore" all our important files to a NEW OS.

---

### Post by mike555 on 2009-09-19
if you have a high speed connection you could use "DropBox" , it gives you about 2 GB free ..

---

### Post by Maintech on 2009-09-19
> if you have a high speed connection you could use "DropBox" , it gives you about 2 GB free .. 

Well, 2 gig isn't very large. Not near enough. I have an 8gig USB drive. But, I have a central home server with much more storage. I just need a simple but effective backup/restore program for Ubuntu that will do incremental backup and do so to a compressed archive. This will allow me to use the same server as a central backup for ALL my computers. There are so many to chose from in the repository it would take weeks to try each one. I thought there might be a Guru who does a lot of this and is experienced with many different ones who would have a suggestion about which one is best for home multi-computer to central server backup. Not enterprise sized in scope which would be overkill. Nice, simple (for my wife), preferably with a GUI but I can script it if necessary. It needs to be incremental and have compression. Restore should be easy and safe (not cause compatibility issues). Again, this isn't for restoring a "crashed" drive. This is mainly for /home directory.

Thank you for the suggestion. Looks like somthing to have for sharing files with my kinfolk. :)

---

### Post by darkstaar on 2009-09-19
You also might want to look at Simple Backup.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by SlugSlug on 2009-09-19
> **darkstaar said:**
> You also might want to look at Simple Backup.

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)


I use simple Backup - its quite nice

---

### Post by Maintech on 2009-09-19
> You also might want to look at Simple Backup.

[https://help.ubuntu.com/community/Ba...pleBackupSuite](https://help.ubuntu.com/community/Ba...pleBackupSuite)

Excellent software for small network. Thank you very much. :guitar:

---

### Post by dcstar on 2009-09-19
> **Maintech said:**
> This question is for the Gurus. Ubuntu comes with a variety of backup software. I have no wish to try them all. The backups will be from several home computers to a central home server. I want to be able to back up /home directory so that after a fresh install I can "restore" the backup to the newer version Ubuntu just installed. This will be in case an "upgrade" doesn't work. 9.04 comes with one installed but have never worked with it. Please include links to any documentation of use with any software recommended.


a) If you have a separate /home partition then a fresh install/reinstall of Ubuntu will not touch your existing user data.

b) The Unison package is quite good for backing up things from a Linux box.

---

