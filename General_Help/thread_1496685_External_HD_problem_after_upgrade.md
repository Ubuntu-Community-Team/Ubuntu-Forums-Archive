---
title: "External HD problem after upgrade"
date: 2010-05-29
forum: General Help
---

### Post by broonsparrow on 2010-05-29
Hi. I have an external HD. I upgraded to 10.4 (while I did this the external HD wasn't swirch on). When I switched on there's two drives in Media: "Backup" (the original name for the external HD) and a new one "Backup_".
I can't open or delete backup and bauckup_ is the wrong path name so prgrammes won't find files on it. How can I delete Backup and change the name of backup_? TIA

---

### Post by lmarmisa on 2010-05-29
Disconnect your external drive, open a terminal and type this command:

> 
sudo rm -r /media/Backup*


Then reboot your system and check if the problem is solved.

---

### Post by broonsparrow on 2010-05-29
worked like a dream. Thanks

---

