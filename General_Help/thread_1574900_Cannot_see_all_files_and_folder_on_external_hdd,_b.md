---
title: "Cannot see all files and folder on external hdd, but Window$ can."
date: 2010-09-14
forum: General Help
---

### Post by buixuanduong1983 on 2010-09-14
Hi everybody,

I'm using Ubuntu 10.04, kernel 2.6.32-25-generic, everything works fine until today I plugged an external hard disk (Transcend 250G), NTFS, only 1 partition, no security software or configuration, on that have about 95G data. The strange thing is I can only see some of the files, total about 72G. I still can copy files and folders there, but cannot see them. But if I plugged it on Window$ then I can see everything normal.  See the screen shoot. Has anybody had this before?

Thanks.

---

### Post by asmoore82 on 2010-09-14
I would run the filesystem check in window$ and mount/unmount the filesystem 2 cycles.

---

### Post by buixuanduong1983 on 2010-09-14
Thanks asmoore82, I ran chkdsk /f on Window$, it fixed some error (delete some index entries, correct something in the master file table bitmap...) and now in Ubuntu I can see everything. Next time if I got same problem I will try Disk Utility on System/Administration first to see if Ubuntu can fix it (forgot to use this tool before).

Thank you. Problem solved.

---

