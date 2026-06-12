---
title: "Removing harddisks from the desktop?"
date: 2006-05-18
forum: General Help
---

### Post by Morientes on 2006-05-18
Is it possible to remove the harddisks from the desktop? And maybe place them in some folder or something? My problem is that I have 13 partitions so it takes up quite a lot of room!

---

### Post by kaamos on 2006-05-18
1) edit /etc/fstab to mount the volumes in /mnt/blaablaa instead of /media/blaablaa

or

2) open gconf-editor (use that command in a terminal) and uncheck apps->nautilus->desktop->volumes visible

---

### Post by dg_w on 2006-05-18
or under the options for nautilus untick the option to show them on the desk top  ?

---

### Post by D_frag on 2006-08-16
ok it's unchecked but they still are on MY desktop !! do i have  to change the directory

---

