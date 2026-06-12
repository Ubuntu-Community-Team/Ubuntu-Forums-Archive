---
title: "Suddenly my flash drives think they belong to root"
date: 2011-05-05
forum: General Help
---

### Post by peyre on 2011-05-05
One day recently, when I plug in a flash drive, Xubuntu won't let me write to it unless I open my file manager as root (gksudo thunar).  This happened a few weeks ago, back under 10.10; I didn't say anything because I thought the upgrade to 11.04 might fix it.  But the behavior continues.

If I stick a zip disk in the drive, I can write to it as normal...but a flash drive gives me read-only permission unless I open Thunar as root.  I don't recall doing anything special with my system, except maybe installing MountManager (I've since removed it, but I'm still getting read-only access).

Anyone know what could cause this?

---

### Post by wilee-nilee on 2011-05-05
Rught click the drive icon-properties-permission, make sure it is set as read and write, and you're in the group.

---

### Post by peyre on 2011-05-05
If only that worked.  Permissions shows it belonging to the root user & group, and both the root group and other are set to read-only.  I can change them in Permissions, but when I close and reopen it, it's reset to what it was before--the changes don't stick.  (Yes, I'm doing this as root.)  I probably should have mentioned that earlier, come to think of it.

And of course, I also have to use root to dismount the flash drive.

---

### Post by wilee-nilee on 2011-05-05
v

---

### Post by fdm on 2011-05-05
I know it is a stretch, but have you tried opening your terminal and running "sudo chmod -R 777 {path to mount point}"? You might also try running thunar from the terminal to see if it spits any errors while you change the permissions and close the properties box.

---

### Post by peyre on 2011-05-05
Hey, thanks for the idea!  It didn't work, unfortunately...but it was worth trying.

It didn't error out; it accepted the command and returned me to the prompt.  But I still have read-only access as a user.

---

