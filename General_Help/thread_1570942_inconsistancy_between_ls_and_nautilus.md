---
title: "inconsistancy between ls and nautilus"
date: 2010-09-08
forum: General Help
---

### Post by petereiso on 2010-09-08
G'day

I am new to this forum, thankyou for providing it.

I have a USB hard drive for backups using rdiff-backup  (/media/backups/).

I tried to do a backup last night but rdiff-backup could not find the appropriate destination directory of the drive.  Sue enough a ls of the drive could not find it.   Odd thing is that it is all visible in nautilus !!  An umount and a (re) mount did not help, even a re-boot did not help.

What might I have done wrong?  How may I found out what is wrong?

thanks in advance

cheers 
pete

---

### Post by harrismh777 on 2010-09-08
At the /media/backups/ directory use the following ls command:

   ls -Al

Use  pwd  to make sure you're in the correct directory. Note the minus(-) sign before the Al switch...  ls -Al

Look for the directory /file. If the file has a dot ( . ) at the front of the name that file will not been seen by ls ,   or ls -l  ,  and is sometimes called a hidden file. 

Nautilus is just a graphical front end to the system list-file commands. The system kernel can either stat the file or it can't. 

Try again.

---

### Post by petereiso on 2010-09-08
> **harrismh777 said:**
> At the /media/backups/ directory use the following ls command:

   ls -Al

Use  pwd  to make sure you're in the correct directory. Note the minus(-) sign before the Al switch...  ls -Al
...
Try again.

Thankyou for the rapid response harrismh777.

That is why I an so confused.  I had trie ls -a, but is was not a dot  file.  I tried ls -Al as you suggest, all to no avail.   It does not show up as a dot file in nautilus!  If anything, I  would have expected the cli to be correct.

I might apply my usual fix, that is go and do something else for a bit and come back.  A coldie down the pub is always a good cure, if it doen't clear the mind you don't care anymore.:D

thanks

---

### Post by CharlesA on 2010-09-08
Maybe it was mounted in a different spot.

Post the output of ***mount*** with the drive mounted.

---

### Post by petereiso on 2010-09-09
> **CharlesA said:**
> Maybe it was mounted in a different spot.

Post the output of ***mount*** with the drive mounted.

Charles

That got it, showed mr how silly I can be.

Somehow I had actually created a directory in /media called backups which does have a backup for one area of the 'puter.  The usb drive was being mounted at /media/backups_/.

All sorted now, thanks.

pete

---

### Post by dcstar on 2010-09-09
> **petereiso said:**
> Charles

That got it, showed mr how silly I can be.

Somehow I had actually created a directory in /media called backups which does have a backup for one area of the 'puter.  The usb drive was being mounted at /media/backups_/.

All sorted now, thanks.

pete

Which is why users should **never**, ever play with system folders. /media is a **system** folder for the **system** to mount removable devices, not for users to play in.

---

