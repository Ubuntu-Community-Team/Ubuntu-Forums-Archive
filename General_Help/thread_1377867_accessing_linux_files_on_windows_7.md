---
title: "accessing linux files on windows 7?"
date: 2010-01-10
forum: General Help
---

### Post by princeofnam on 2010-01-10
i can't access linux files from windows 7 no matter what program i use. any luck in this respect?

[http://www.tonyphamilyman.com](http://www.tonyphamilyman.com)

---

### Post by sailthesea on 2010-01-10
In short I don't think you can:(
Windows won't recognise ext3\4 diskspace which is the filesystem Linux uses Linux will however read NTFS files meaning it can read Windows files
 Someone may know a way round this though!
 Keep trying

---

### Post by bluelamp999 on 2010-01-10
You could try [http://www.fs-driver.org/]("http://www.fs-driver.org/") or [http://www.ext2fsd.com/]("http://www.ext2fsd.com/")

But if you're trying to access an ext4 filesystem the above won't work (as yet).

---

### Post by princeofnam on 2010-01-10
blarg.

---

### Post by princeofnam on 2010-01-10
what are the difference among ext2,3, and 4 anyway?

---

### Post by raymondh on 2010-01-10
> **princeofnam said:**
> what are the difference among ext2,3, and 4 anyway?

If you want to read the technical ...

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

The main advantage of ext3 over ext2 is journaling.  

As for ext4, let time tell if the supposed advantages are indeed worth more than the "attained" stability of ext3.

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

