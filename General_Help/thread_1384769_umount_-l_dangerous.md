---
title: "umount -l dangerous?"
date: 2010-01-18
forum: General Help
---

### Post by cthlhu1987 on 2010-01-18
Is the unmounting of an partition via "lazy" unmount more dangerous than regular unmount?

---

### Post by Mark Phelps on 2010-01-19
Yes -- because it attempts to unmount a filesystem that is still being used.  

As long as you're not writing to the filesystem, it's unlikely to do any damage, though.

---

