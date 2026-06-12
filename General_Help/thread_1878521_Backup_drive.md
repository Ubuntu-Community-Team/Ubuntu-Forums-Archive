---
title: "Backup drive"
date: 2011-11-09
forum: General Help
---

### Post by crutch145 on 2011-11-09
I am running Ubuntu 11.10.  I have a second hard drive that I use as a backup drive.  I originally named it BACKUP.  It showed in the /media directory.  However, now it shows three times in the media directory, with extra underscores after the name - BACKUP_ and BACKUP__.  The BACKUP__ is the one that shows a small hard drive symbol on it.  How can I delete these and just use the BACKUP without the underscores (_)?  

Thanks,

Justin

---

### Post by crutch145 on 2011-11-09
I solved this with sudo rm -rf /media/BACKUP (found this from user iaculallad on a different thread).  Thanks!

---

