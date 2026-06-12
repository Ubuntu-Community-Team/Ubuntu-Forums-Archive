---
title: "transmission nt working well Torrent"
date: 2011-04-05
forum: General Help
---

### Post by gabak on 2011-04-05
good morning.
i got two hdd one of 160gb and other 1tb.
and i m getting these errors i dont know why, for instance ElementaryOS.ISO it was downloading ok yesterday at night and today at morning it was nt and it show up that error.! why is that i mean it seem like it is a problem with permission but should nt be it was working 5 hours ago.

have nice day.

pd: i m saving everything in 1tb hdd, i had this problem with the version that comes with ubuntu 10.10 and now i updated and i still have the same problem

---

### Post by Grenage on 2011-04-05
When you get those errors, are you able to manually read/write to /media/1tb?

---

### Post by gabak on 2011-04-05
i just tried and i could nt read any file and either delete.
i have two user mine was the first one the second one it for my wife.

---

### Post by Grenage on 2011-04-05
Is the drive ever accessible?  I'm going to assume that this is either a permissions issue, or a failing drive; probably the latter.  Do you currently have any data on the drive, and if so where was the drive formatted/used.

From a command line:

```
sudo fdisk -l
```

I'm curious as to what FS it's using.

---

