---
title: "Read Windows drive from WUBI Ubuntu Installation"
date: 2010-10-22
forum: General Help
---

### Post by arjunbajaj on 2010-10-22
Hello,

I installed ubuntu by WUBI on windows...
now i want to read and write on my windows drive where ubuntu is installed... but i want to view other things like the softwares installed in windows...

how should i do that??

thnx...

---

### Post by yetiman64 on 2010-10-22
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?")


You could check out the above link_[U] apparently__ Windows is under /host _[/U](places > computer > file system > host) _[U]or other partitions are under _[/U]places > removable media.

---

### Post by gchand7 on 2010-10-22
You should have created a separate partition before you installed it then when when it ask where to put ubuntu you could choose the designated area then when you go to *places* *computer* it would show the windows partition and you could access folders. I'm sure that a more experienced user has a better way but thats how I do it.

---

### Post by yetiman64 on 2010-10-22
> **gchand7 said:**
> **You should have created a separate partition** before you installed it then when when it ask where to put ubuntu you could choose the designated area then when you go to *places* *computer* it would show the windows partition and you could access folders. I'm sure that a more experienced user has a better way but thats how I do it.

A separate partition is not a wubi install as the OP is talking about, wubi is Ubuntu installed into a file within the Windows NTFS filesystem and can be removed from Windows just like a normal Windows program.

---

