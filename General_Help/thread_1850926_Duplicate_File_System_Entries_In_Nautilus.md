---
title: "Duplicate File System Entries In Nautilus"
date: 2011-09-27
forum: General Help
---

### Post by jdjacobs on 2011-09-27
Using Natty there are two entries in the Nautilus' Places menu for my "DOS" file system.  One entry is the file system that /etc/fstab mounts.  The other entry is useless--when I click it, an error message indicates that the file system is already mounted.  The duplicate entry also appears in the Places menu item on Natty's panel (I have reverted to the standard Gnome interface.)  How can I delete this duplicate entry?  (This duplicate entry is not part of the bookmark entries in Nautilus that you can edit.)

---

### Post by ajgreeny on 2011-09-27
Have you at some point manually mounted the file system at a folder you made yourself?

---

### Post by blueridgedog on 2011-09-27
Is it listed twice in /etc/fstab?

---

### Post by oldfred on 2011-09-27
It shows partitions mounted in /home or /media twice. 

One work around there was in fstab to replace UUID=xxxx with
/dev/disk/by-uuid/xxxx

---

### Post by Habitual on 2011-09-27
> **jdjacobs said:**
> One entry is the file system that /etc/fstab mounts.  The other entry is useless--when I click it, an error message indicates that the file system is already mounted.  The duplicate entry also appears in the Places menu item on Natty's panel (I have reverted to the standard Gnome interface.)  How can I delete this duplicate entry?  (This duplicate entry is not part of the bookmark entries in Nautilus that you can edit.)

Open nautilus bookmarks and peek around.

---

