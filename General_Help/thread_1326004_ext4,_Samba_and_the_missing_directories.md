---
title: "ext4, Samba and the missing directories"
date: 2009-11-14
forum: General Help
---

### Post by vtk on 2009-11-14
Heyas all,

I'm trying to maintain my calm.  I am running 9.10 with two brand new ext4 on Seagate drives.  I have had 2 directories disappear.  One directory was just named 'old' so I could have easily destroyed it, when I realized the entire directory for my World Of Warcraft was also missing.  I could have deleted one dir, but two, one with a name like World of Warcraft?

I was creating and removing test shares with Samba when I noticed these directories were missing.  I've unmounted all shares for this recovery.

There was nothing in the 'trash can'.

Does anyone know about disappearing directories in 9.10 or how I might be able to recover these directories?  Sort of losing it tonight...

Peace,
V

---

### Post by slimx3m on 2009-11-14
were you in the terminal whenever you were working with the samba shares?

---

### Post by vtk on 2009-11-14
Actually, yes I was.  I created some of the Samba shares via vimming smb.conf directly.

---

### Post by ultratek on 2010-01-17
look up the inodes for the missing files/dirs and use debugfs to undelete

---

