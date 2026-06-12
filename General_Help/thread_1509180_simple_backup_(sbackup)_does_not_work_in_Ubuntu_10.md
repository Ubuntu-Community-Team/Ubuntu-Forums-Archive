---
title: "simple backup (sbackup) does not work in Ubuntu 10.04"
date: 2010-06-13
forum: General Help
---

### Post by JBA2337 on 2010-06-13
Simple Backup (sbackup) does not work at all in Ubuntu 10.04. It worked fine in version 9.04 and previous versions, but after upgrading to version 10.04 sbackup no longer works. If I try to run a backup, the program tells me that "a backup run is initiated", but nothing happens. No backup.

I uninstalled sbackup and then reinstalled it, but this did not help.

Any idea how to fix this?

JBA2337

---

### Post by Selwynbear on 2010-06-15
> **JBA2337 said:**
> Simple Backup (sbackup) does not work at all in Ubuntu 10.04. It worked fine in version 9.04 and previous versions, but after upgrading to version 10.04 sbackup no longer works. If I try to run a backup, the program tells me that "a backup run is initiated", but nothing happens. No backup.

I uninstalled sbackup and then reinstalled it, but this did not help.

Any idea how to fix this?

JBA2337

[http://wwww.ubuntuforums.org/showthread.php?t=1480520](http://wwww.ubuntuforums.org/showthread.php?t=1480520)

Sudo sbackupd worked for me, put the file where I had set it up in the GUI.

Not ideal, and no guarantees about restores being perfect, as I have only had the chance to do basic tests.

---

