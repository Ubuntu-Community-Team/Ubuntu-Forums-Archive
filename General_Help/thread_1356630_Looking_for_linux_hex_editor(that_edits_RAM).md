---
title: "Looking for linux hex editor(that edits RAM)"
date: 2009-12-16
forum: General Help
---

### Post by module0000 on 2009-12-16
Anyone aware of one of these?  My googling isn't turning up what I'm looking for.

To clarify what I am looking for...I am not looking for a hex editor to edit files.  I'm looking for something to search used memory for values and replace them.

Anyone familiar with a program of this sort for linux?

---

### Post by doas777 on 2009-12-16
you could write it to a file first:
```
sudo cat /dev/ram0 > ~/ram

```

---

