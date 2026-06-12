---
title: "Missing directories in Nautilus after copy"
date: 2010-01-23
forum: General Help
---

### Post by kendallp on 2010-01-23
I recently copied some directories from a Windows Vista box that I wanted to backup on my linux box.  I used Nautilus to copy the directories and everything seemed to work fine.  When I later tried to access the directories in Nautilus they are not there.  I can see them if I look in the terminal using "ls" and I can also see them with my windows machine via samba.

There are other directories in this folder I can see in Nautilus and it looks like the permissions are the same on the folders that show and the ones that do not.

Also in a separate issue, when I use ls on the directory in questions it has two directories it gives an error on before my listing.  Error looks like this when I run "ls -l" compared to both directories I can see in Nautilus and ones I can not:

```
ls: cannot access Directory1: Input/output error

d????????? ? ?    ?    ?                    ? Directory1
drwxrwxrwx 1 root root 40960 2008-08-12 21:32 ICanSeeInNatuilus
drwxrwxrwx 1 root root 28672 2010-01-23 09:35 ICanNotSeeInNautilus
```



Thanks everyone in advance,
-Kendall

---

### Post by kendallp on 2010-01-23
bump

---

### Post by dcstar on 2010-01-23
> **kendallp said:**
> I recently copied some directories from a Windows Vista box that I wanted to backup on my linux box.  I used Nautilus to copy the directories and everything seemed to work fine.  When I later tried to access the directories in Nautilus they are not there.  I can see them if I look in the terminal using "ls" and I can also see them with my windows machine via samba.

There are other directories in this folder I can see in Nautilus and it looks like the permissions are the same on the folders that show and the ones that do not.

Also in a separate issue, when I use ls on the directory in questions it has two directories it gives an error on before my listing.  Error looks like this when I run "ls -l" compared to both directories I can see in Nautilus and ones I can not:

```
ls: cannot access Directory1: Input/output error

d????????? ? ?    ?    ?                    ? Directory1
drwxrwxrwx 1 root root 40960 2008-08-12 21:32 ICanSeeInNatuilus
drwxrwxrwx 1 root root 28672 2010-01-23 09:35 ICanNotSeeInNautilus
```



Thanks everyone in advance,
-Kendall

Did you correctly unmount any external media and **wait** for it to finish writing?

Run a **fsck** on the filesystem.

---

### Post by kendallp on 2010-01-23
Thanks for the response David.

I did wait for the copy to finish (there was a 30 min lag between when it finished and I checked the computer).  I ran fsck and there were no errors.

Here is some additional info:

This is a secondary harddrive on my linux box that I manually mount.  It is an old drive out of a windows box so has an NTFS file system.

If I copy the directory (using cp) the directory now shows in Nautilus.  If I rename the directory (using mv) it shows initially in Nautilus but once I unmount and remount the drive it is no longer available.


EDIT:  I just copied another directory using cp and when I mount and unmount it hardrive I no longer see the new directory in Nautilus but it is still shows using ls.  Even more confused now.


Thanks again,
-Kendall

---

