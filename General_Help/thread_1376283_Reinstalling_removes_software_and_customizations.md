---
title: "Reinstalling removes software and customizations?"
date: 2010-01-09
forum: General Help
---

### Post by wirate on 2010-01-09
I have broken up my ubuntu installation by deleting some system files. I would like to reinstall on the same partition without formatting. Will this remove my installed software and configurations?
Thanks

---

### Post by wirate on 2010-01-10
bump?

---

### Post by wirate on 2010-01-13
come on?????

---

### Post by cong06 on 2010-01-13
I think that no one really wants to touch this question....
Maybe you should assume it does, try it, and if it doesn't you don't have to restore.

---

### Post by konqueror7 on 2010-01-13
the most important to backup is your home folder, it contains most of your applications configs, next is you can backup all installed applications into a list, then reinstall it again after,,,

could your perhaps define what you mean by 'broken', maybe we can still fix it?

---

### Post by Jive Turkey on 2010-01-13
If by "deleting some files" you mean some files in your home directory, particularly ones that start with "." then you could try opening a terminal and type 
```
sudo adduser <blah>
```
Answer the questions and when done log out and in as the new user.  If things work we might be ok.  If not there may be a reinstall in order, but maybe not.

---

### Post by wirate on 2010-01-13
This is broken :)

[http://ubuntuforums.org/showthread.php?t=1373657](http://ubuntuforums.org/showthread.php?t=1373657)

[http://ubuntuforums.org/showthread.php?t=1367975](http://ubuntuforums.org/showthread.php?t=1367975)

---

### Post by eriqjaffe on 2010-01-13
To answer your question - yes.  Reinstalling Ubuntu will blow away your installed programs.

I'd suggest looking into APTonCD in order to "back up" your programs, but if you're having trouble installing anything, you may not be able to use that.

If your home directory is on another partition, it'll be safe.  If not, it won't be - back it up to an external drive, flash drive, stack of CD's, whatever you can.

---

