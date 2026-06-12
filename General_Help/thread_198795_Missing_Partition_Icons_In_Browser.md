---
title: "Missing Partition Icons In Browser"
date: 2006-06-17
forum: General Help
---

### Post by leadweight on 2006-06-17
When I click on "Computer" in the file browser, several of the Icons are missing.

I tried "killall nautilus" suggested elswhere around here and that did not work.

Any ideas?

---

### Post by leadweight on 2006-06-17
[QUOTE=leadweight]When I click on "Computer" in the file browser, several of the Icons are missing.

I tried "killall nautilus" suggested elswhere around here and that did not work.

Any ideas?[/QUOTE]


OK, it seems the partitions are the Windows ones that I am mounting via editing fstab.  Commenting out the lines brings back the partitions, but then they do not mount.

either this is related to the recent updates, or am I mounting them wrong?

---

### Post by MarinaraOfDeath on 2006-06-17
[QUOTE=leadweight]OK, it seems the partitions are the Windows ones that I am mounting via editing fstab.  Commenting out the lines brings back the partitions, but then they do not mount.

either this is related to the recent updates, or am I mounting them wrong?[/QUOTE]

Can you not mount them using the partitions tab in System->Administration->Disks->Hard Disk (in Gnome)? If in KDE, then it's even easier, just go to System Settings->Disks and Filesystems. Just enable and go, though you may want to change them to be owned by your user account instead of root if you want read/write access everywhere.

---

### Post by leadweight on 2006-06-18
Problem solved, mount point changed to /media

---

