---
title: "Searching tool/command to view disc space consumption by dirs?"
date: 2010-01-28
forum: General Help
---

### Post by pstein on 2010-01-28
I am searching a GUI based "tree view utility" which shows me which directories consume how much hard disc space (cumulative, including recursively the sub directories; including hidden files). 
 
Is there such a tool fur Ubuntu/Linux and how do I install it?
 
Is there at least a cmdline command which does the same job in terminal window?
 
Peter

---

### Post by sisco311 on 2010-01-28
> **pstein said:**
> I am searching a GUI based "tree view utility" which shows me which directories consume how much hard disc space (cumulative, including recursively the sub directories; including hidden files). 
 
Is there such a tool fur Ubuntu/Linux and how do I install it?
 
Peter

Yes, [baobab]("apt://gnome-utils"), click the apturl link to install it or use your favorite package manager to install the gnome-utils package. To run it, go to Applications -> Accessories -> Disk Usage Analyzer. 

> **pstein said:**
> 
Is there at least a cmdline command which does the same job in terminal window?


```
du -chs /path/to/dir
```

---

