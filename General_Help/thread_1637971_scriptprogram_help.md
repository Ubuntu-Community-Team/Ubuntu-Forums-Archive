---
title: "script/program help"
date: 2010-12-05
forum: General Help
---

### Post by jfreak_ on 2010-12-05
I need help to write a script which generates files which are Gb's in size. The easiest thing I can think of is a huge loop which does nothing except print hello world to a file, but I am sure there are more effective ways to do it.

---

### Post by DaithiF on 2010-12-05
something like this:
```
dd if=/dev/zero bs=1M count=1K of=my1gbfile
```
will create a file filled with zeros, adjust bs (bytes to read/write at a time), or count (number of blocks to read/write) to achieve the desired size

---

### Post by drewsus on 2010-12-05
Im curious as to why you want to do this? To hide your tracks?

---

### Post by jfreak_ on 2010-12-05
> **drewsus said:**
> Im curious as to why you want to do this? To hide your tracks?

no wrong answer, if I tell you guys the real answer you wont believe me.

---

### Post by drewsus on 2010-12-05
You'd be surprised. I've probably believed 40 unbelievable things in a day before you've even had breakfast.

---

