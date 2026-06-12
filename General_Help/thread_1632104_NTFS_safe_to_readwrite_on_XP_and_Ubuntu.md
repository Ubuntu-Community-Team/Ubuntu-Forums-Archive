---
title: "NTFS safe to read/write on XP and Ubuntu?"
date: 2010-11-27
forum: General Help
---

### Post by Karut on 2010-11-27
If I have an external hard drive NTFS it is as safe to read/write on it from either Win XP and Ubuntu?

---

### Post by CharlesA on 2010-11-27
It should be, yes. There can be hiccups, but for the most part it's fine.

---

### Post by Karut on 2010-11-28
Hiccups :D

I just want to ensure that my personal data does not get corrupted. Of course I have a backup, but this is also NTFS then. 

Data integrity is quite important and has to be taken into consideration when I boot dual :)

---

### Post by WorMzy on 2010-11-28
NTFS is the ideal choice for a shared partition, as it can be read and written to from either Windows or Linux. One of the down sides of NTFS is that it doesn't support Linux file permissions, so these have to be set at boot time. This tutorial should explain how to do that: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251").

---

### Post by CharlesA on 2010-11-28
> **Karut said:**
> Hiccups :D

I just want to ensure that my personal data does not get corrupted. Of course I have a backup, but this is also NTFS then. 

Data integrity is quite important and has to be taken into consideration when I boot dual :)
Hiccups as in you lost power while the drive was mounted and now you need to boot into Windows to run chdisk on it before you can mount it again.

---

### Post by Karut on 2010-11-28
Ah alright thanks for your clarifying words :)

---

