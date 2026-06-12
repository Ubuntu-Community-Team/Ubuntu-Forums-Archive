---
title: "terminal command help"
date: 2009-12-21
forum: General Help
---

### Post by McGuffin on 2009-12-21
So when I open terminal it defaults to my home directory, and I can move around inside the ubuntu filesystem no problem.

But I have a storage partition set up - how do I cd to the directories in the other partition?

Thanks

McG

---

### Post by konqueror7 on 2009-12-21
> **McGuffin said:**
> So when I open terminal it defaults to my home directory, and I can move around inside the ubuntu filesystem no problem.

But I have a storage partition set up - how do I cd to the directories in the other partition?

Thanks

McG

you may want to read [Mounting Partitions In Ubuntu Automatically]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"). if you have already mounted your partition, you may use 
```
cd /media/**MyStorage**
``` or ```
cd /mnt/**MyStorage**
```
these are default locations.

---

### Post by byStanderone on 2009-12-21
...[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by McGuffin on 2009-12-21
Thanks guys.

---

