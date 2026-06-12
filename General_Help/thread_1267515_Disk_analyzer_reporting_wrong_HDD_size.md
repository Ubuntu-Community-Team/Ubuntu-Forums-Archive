---
title: "Disk analyzer reporting wrong HDD size"
date: 2009-09-15
forum: General Help
---

### Post by goldenflames95 on 2009-09-15
I am running Jaunty and Disk analyzer is reporting that I have a 70gig HDD when in fact i have a 320gig seagate. any reason why?

---

### Post by hwttdz on 2009-09-17
What is disk analyser?  pysdm? gparted? du?  Anyways, you should investigate all 3 and see if you can figure out what's going on.  I think one of them will probably enlighten you.

---

### Post by dcstar on 2009-09-18
> **goldenflames95 said:**
> I am running Jaunty and Disk analyzer is reporting that I have a 70gig HDD when in fact i have a 320gig seagate. any reason why?

Disk Usage Analyzer reports on your available filesystems in User mode.

If you want full reporting you must launch it with root privileges:

```
gksudo baobab
```

---

