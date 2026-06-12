---
title: "Removing parent dirs from tar"
date: 2011-07-30
forum: General Help
---

### Post by Jonny87 on 2011-07-30
I'm trying to use tar which I've used a bit before but have never had to do this so I'm unsure. I'm trying to remove parent dirs from the backup.
example;
```
tar cvpjf /path/to/backup.tar.bz2 /path/to/the/source
```I want the backup.tar.bz2 to only contain the contents of source. At the moment the contents of the backup.tar.bz2 have the following file structure /path/to/the/source/files.

How can I remove the parent dirs from the backup.tar.bz2?

Alternatively, How could I just extract the contents of source with out the above folder structure? at the moment when I extract the backup.tar.bz2, I get the full folder structure in the location that I extracted it to.

---

### Post by relay_man on 2011-07-31
Someone who is better at this than I am will have to answer your question about removing the parent directories from your existing archive. In answer to your second question, I found this:

 [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Although it is geared towards how to create a complete system backup, It appears to show everything needed to help you craft a command that will  backup just the contents of the directories of interest.

Hope this helps

---

### Post by AlphaLexman on 2011-07-31
I don't completely understand your request...

You want to create a tarball of a directory, but you don't want to maintain the (sub)-directory structure ??

You could try the '**--no-recursion**' or the '**--recursive-unlink**' options.

---

