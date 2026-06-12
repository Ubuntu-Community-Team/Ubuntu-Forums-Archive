---
title: "Mount Permissions?"
date: 2010-10-18
forum: General Help
---

### Post by Daemn on 2010-10-18
Hi!

Recently I've been unable to set file permissions. Basic 10.10 install, all I've done is installed some stuff (all GNOME). I'm trying to run a .exe with Wine. It worked yesterday. I right-click, go to Permissions tab, click "Allow executing file as program" and it shows it checked then instantly un-checks it. I thought it might be the UI, but I used shell to recursive chmod, and it did it for a few minutes but still the same permissions. It does that for Group/Other access as well. I only have Read/Write for my user. I can't even change it to just Read. I have no permissions to change anything on this mount. It's just another SATA drive (NTFS).

Thanks for any clues you can give me

---

### Post by sikander3786 on 2010-10-18
You can try removing the **noexec** flag from the mount's properties in fstab.

See here for details.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

