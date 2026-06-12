---
title: "One of my Folders Contains 128TB"
date: 2010-06-12
forum: General Help
---

### Post by Penguin Guy on 2010-06-12
Nautilus just reported to me that a folder (chromiumos.git) on my 80GB hard disk contains 128TBs of information:
```
585,184 items, totalling 128.0 TB
```
What's going on?

EDIT: This seems to be a one off, so I'll mark it as solved - although I am still curious.

---

### Post by Ioky on 2010-10-08
You are not the only one. Something is wrong, my root directory show this number. It is a bug. You really should unsolved this

---

### Post by UnterUn on 2010-10-08
I agree with Ioky. Could be a problem if you need to know what your system size is.

I found by also usingNautilus and right clicking --> 'properties' on system it jumps up to 128TB after (logically) increasing from zero as the files are counted - and ceases to rise any further.

Either way its reproducible so i'll report it as a bug if you haven't already.

---

### Post by Penguin Guy on 2010-10-09
It looks like this has been reported as [bug #585472]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472").

---

