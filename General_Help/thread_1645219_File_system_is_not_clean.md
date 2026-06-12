---
title: "File system is not clean?"
date: 2010-12-14
forum: General Help
---

### Post by gunit888 on 2010-12-14
I have a 500 GB external USB hard drive that I use for putting images and backup data into.  I had some problems with it not automounting today, and in trying to access the drive I got errors indicating that an operation was already in progress.  Eventually it mounted on it's own, but I unmounted it and ran "Check Filesystem" from the Disk Utility program on the drive, just to be sure.  After a while, it finished and told me that the file system was "NOT clean".

So, what does that mean, and how do I fix it?  Before I unmounted it, I was able to navigate the mounted filesystem, so it doesn't appear totally hosed.

---

### Post by dabl on 2010-12-14
Boot your Live CD, run GParted, navigate to the drive in question, right-click the graphic and choose "check", and then do "Apply".

Might was well do the internal drive(s) while you're at it.

Here's a great resource for such purposes, btw:  [http://sourceforge.net/projects/partedmagic/files/partedmagic/](http://sourceforge.net/projects/partedmagic/files/partedmagic/)


Note that a partition must be unmounted in order to be checked.

---

### Post by gunit888 on 2010-12-14
Well, it appears to have worked.  Somehow, my lost+found directory got destroyed, so I am guessing that was the problem.

Thanks!

---

