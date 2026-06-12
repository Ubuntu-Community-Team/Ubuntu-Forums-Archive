---
title: "CD wont eject after music extracting failure"
date: 2011-07-01
forum: General Help
---

### Post by aninona on 2011-07-01
tried to extract  some music using cd juicer[cli: sound-juicer]

now the tray wont open.

What shall I do?

tnx!!:lolflag:

---

### Post by dino99 on 2011-07-01
your reader should have a thin hole to insert something thin too to push on

---

### Post by nothingspecial on 2011-07-01
Try opening a terminal and typing

```
eject -V
```

That's a big V

are there any errors?

---

### Post by mikejonesey on 2011-07-01
```
sudo umount /media/cdrom1
```
should auto eject, or just right click the icon and safley remove / eject...

---

### Post by aninona on 2011-07-01
> **dino99 said:**
> your reader should have a thin hole to insert something thin too to push on

that worked tnx,

now the tray wont come back using cli/button, only manually pushing it :P

what should I do?

:P

---

