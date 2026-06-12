---
title: "Proper way to remove Ubuntu?"
date: 2009-08-26
forum: General Help
---

### Post by johnnydotexe on 2009-08-26
On a dual boot system, what would be the proper way to remove Ubuntu + Windows and put the HDD back to one NTFS partition?

Reason I ask is because I may sell my laptop to a friend that needs one more than I do currently, and I'm running XP + Ubuntu 9.04 on it right now.  I want to wipe the HDD and get it back to one blank NTFS partition, ready for him to install whatever OS he wants...most likely windows.

Can I use DBAN, or gparted as liveuser to do this safely/properly?

---

### Post by lisati on 2009-08-26
If you are likely to get rid of your laptop, a simple solution would be to do a fresh install of Windows from the recovery partition or recovery disk. Don't forget to backup your data first.

---

### Post by Primefalcon on 2009-08-26
if you want blank probably easiest just to run the XP disc itself and wipe all the partitions and then create a new one and format and leave it at that.... Windows makes the ntfs partitions kinda just for windows so you're better off using a windows tool if you can, otherwise just boot a Ubuntu live disk and do it in the partition editor under system -> admin

make sure everything is unmounted and swap is off, then delete everything, create one ntfs partition and format and then, well your done, windows would prob want to reformat it though when he goes to install but what the hey

---

