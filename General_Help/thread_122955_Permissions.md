---
title: "Permissions"
date: 2006-01-28
forum: General Help
---

### Post by DopeShow on 2006-01-28
hi. 
i instaled ubuntu today. i've other particion FAT32 and i can't write on it.
could anyone help?

tkx

---

### Post by mstlyevil on 2006-01-28
[QUOTE=DopeShow]hi. 
i instaled ubuntu today. i've other particion FAT32 and i can't write on it.
could anyone help?

tkx[/QUOTE]

Go to system<administration<disk manager then click on the partitions tab. Click on each partition until you get to the one that is FAT32. If it says inaccessible then click on the enable button and see if that does not enable you to write to that partition.

---

### Post by cotcot on 2006-01-29
Check the name of your fat partition: let us suppose it is hda4.
Make a directory to mount your fat partition to , for instance : mkdir windows 

Add a line to etc/fstab (cp /etc/fstab /etc/fstabold to backup your actual fstab;  then sudo gedit /etc/fstab and save)  :

/dev/hda4       /home/xxx/windows  vfat    iocharset=utf8,umask=000   0       0

(xxx is your name)

This will mount your Fat partition each time you boot your computer.

---

### Post by aysiu on 2006-01-29
See the fourth link of my signature.

---

