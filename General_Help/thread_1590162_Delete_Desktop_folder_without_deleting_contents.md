---
title: "Delete Desktop folder without deleting contents"
date: 2010-10-07
forum: General Help
---

### Post by rUFFn3k on 2010-10-07
Im assuming there is a simple answer for this but I have yet to find it in forums. I have 2 partitions mounted on my ubuntu desktop, one is Windows C: drive labeled "Core" and the other is D: drive labeled "Reserve" but for some reason I have a second Windows folder on my desktop, when I attempted to delete it it began to delete the Windows files as well, one forum said to right click and "remove from desktop" but this option isnt in the menu. How can I just delete the folder?


[IMG]http://i667.photobucket.com/albums/vv40/ruffn3k/Screenshot.png[/IMG]

---

### Post by PapaNerd on 2010-10-07
Do the files in that folder correspond to those in either your Core or Reserve partitions?
Please post the output from the ```
df -h
``` command so we can see if it is a mounted file system.  One quick and dirty option would be to open a terminal window (which puts you in your home directory) and then ```
cd Desktop
mv Windows ..
``` which places the folder in the home directory instead of on the desktop.

---

### Post by rUFFn3k on 2010-10-07
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              93G   73G   16G  83% /
none                  2.0G  320K  2.0G   1% /dev
none                  2.0G 1000K  2.0G   1% /dev/shm
none                  2.0G  192K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda2             137G   83G   54G  61% /media/Windows
/dev/sda3             232G   80G  153G  35% /media/Reserve
/dev/sda5              92M   39M   48M  46% /boot

Yes the folder corresponds to the Windows partition.

---

