---
title: "Newbie Q. Saving to Win2000 partition."
date: 2006-02-18
forum: General Help
---

### Post by b_chris on 2006-02-18
Hello,

As I can move files from Win200 partition to Ubuntu, can I go the other way and save to the Win2000 partition??

I have tried CHMOD 777 and also made shaw sharing was on in windows, but still nothing.

Can this be done??

regards.

---

### Post by cilynx on 2006-02-18
It depends.

Win2k can be installed on either Fat32 or NTFS.  Linux can read and write Fat32 with no problem.  Linux can read NTFS, but write support is extremely limited at best.  If your Win2k is on NTFS, you're pretty much S.O.L..

As I've explained in some other threads, Fat32 is the holy grail of sharing between Linux and Windows.

---

### Post by FizDev on 2006-02-18
I haven't tried it, but maybe you can follow this howto :
[http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)

I have NO idea if it will work, so you should backup important data before doing anything.

---

### Post by b_chris on 2006-02-18
My Win2000 partition is formated FAT32.

Thanks for your help guys.

---

### Post by cilynx on 2006-02-18
Then you should be able to write to it with no problem.  What's the error it's throwing at you?

---

### Post by b_chris on 2006-02-22
Permission denied.

Anyway, found these:

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

Thanks again people.

regards.

---

### Post by LordBug on 2006-02-22
Much like NTFS, you need to use the umask option for FAT mounting:

> umask=value 
Set the umask (the bitmask of the permissions that are not present). The default is the umask of the current process. The value is given in octal

---

