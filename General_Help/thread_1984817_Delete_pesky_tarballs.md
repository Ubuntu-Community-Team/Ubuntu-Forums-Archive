---
title: "Delete pesky tarballs"
date: 2012-05-22
forum: General Help
---

### Post by Goldpin on 2012-05-22
Here we go again!  I've tried backing up my system using a method described in one of the forums.  (The Heliode guide to successful backing-up and restoring of a Linux system!).  However, I got one of the commands wrong and now have a couple of tarballs (*.tar.bz2) I'm trying to delete.  For some reason, I can't get rid of them (even as root).:confused:  They are quite large (several Gigs).  Any suggestions?????

Thanks in advance.

---

### Post by hal8000 on 2012-05-22
From the terminal, change into the directory where the tarballs are kept and post output of:

sudo ls -l

---

### Post by Goldpin on 2012-05-22
> **hal8000 said:**
> From the terminal, change into the directory where the tarballs are kept and post output of:

sudo ls -l
Here's the information:

-rw-rw-rw- 1 merle merle  773013504 2012-05-22 14:41 backup20120522.3.tar.bz2
-rw-rw-rw- 1 merle merle 6777995264 2012-05-22 14:42 backup20120522.tar.bz2
-rw-rw-rw- 1 merle merle 5776568320 2012-05-22 14:37 files.tar.bz2
 
I've changed the permissions so they are no longer root.  I will also add that the files are located in:

root/.local/share/Trash/files

Whenever I try deleting them, the disappear for about a second and then reappear with a slightly different filename.

---

