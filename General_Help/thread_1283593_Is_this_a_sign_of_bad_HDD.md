---
title: "Is this a sign of bad HDD?"
date: 2009-10-05
forum: General Help
---

### Post by dustyg54 on 2009-10-05
I ran ```
sudo badblocks /dev/sda
```
and 212 numbers (such as 72023165) showed up in the terminal.  Is there a way to repair these blocks?

---

### Post by Giblet5 on 2009-10-05
```
man e2fsck
```

You can pass a badblock list.

---

