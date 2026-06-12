---
title: "free space on hardrive"
date: 2009-10-02
forum: General Help
---

### Post by kapad on 2009-10-02
since the pas few months i have noticed that the free space reported by nautilius is not the same as the free space reported by disk usage analyzer. 

also if i add up everything manually and then subtract that from the hard drive capacity it seems to me that i should have more free disk space on the drive than nautilius reports.

another thing i have noticed is that whenever i run partition manager when booting from the internal hdd it says that there is no mount point that it can find on the filesysytem i.e. the ext3 filesystem

anyone who can explain part of this or the whole thing to me please reply. also if there is something drastically wrong in not having a mount point recognized by partition manager please let me know how i should correct this.

thanx

---

### Post by kapad on 2009-10-02
bump

---

### Post by khelben1979 on 2009-10-02
Do you mean [Baobab]("http://en.wikipedia.org/wiki/Disk_Usage_Analyzer")?

I don't know much about the accuracy of these applications. Use the ```
df -h
``` to see your available disk space instead.

---

