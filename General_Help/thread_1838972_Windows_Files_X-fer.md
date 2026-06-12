---
title: "Windows Files X-fer"
date: 2011-09-04
forum: General Help
---

### Post by congleal on 2011-09-04
I've just recent jumped ship from Windows to Ubuntu.  I am running the Ubuntu Desktop 11.4 with Apache2, MqSQL, PHP, etc.  I've got an enormous number of web files that I am trying to migrate from Windows to Apache2.  I am having some serious issues concerning file ownership and being able to read and see the web data because of "ownership".  There's got to be a better way to move these files without having to change ownership on every file?

Help! Novice:confused:

---

### Post by Mark Phelps on 2011-09-05
You don't say how you're accessing the file but if you're using Nautilus, try running it as root and seeing if that bypassed the ownership problems.

Myself, I prefer using Gnome-Commander because of its two-panel arrangement -- either vertical or horizontal panels, with each panel pointing to a different location.  You can then just drag-and-drop files from one panel to another.  And when I run that as root, I don't encounter any ownership problems dragging files from my NTFS partitions.

---

### Post by gordintoronto on 2011-09-05
I can open terminal, cd to the folder where there are files (and folders) with bad ownership, and enter this command:
sudo chown -cR gord *

Don't do it in a system folder!

(chown is "change owner." "gord" is my userid.)

---

