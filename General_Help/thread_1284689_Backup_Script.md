---
title: "Backup Script"
date: 2009-10-06
forum: General Help
---

### Post by jmauld on 2009-10-06
On my network, I have a Samba NAS that I use to store files accessible from all computers.

I'd like to use my linux computer to make backups of the Samba shared folders.  I have a BASH script that will make local file backups, but I can't figure out how to make it access the Samba shared folders.

Do you guys have any suggestions on how I can do this, within a single script?

---

### Post by c0mput3r_n3rD on 2009-10-06
> **jmauld said:**
> On my network, I have a Samba NAS that I use to store files accessible from all computers.

I'd like to use my linux computer to make backups of the Samba shared folders.  I have a BASH script that will make local file backups, but I can't figure out how to make it access the Samba shared folders.

Do you guys have any suggestions on how I can do this, within a single script?

Post this script, and make a link to it in the programming section.  You probably just need a few lines of code put in.

---

### Post by renkinjutsu on 2009-10-06
Are these samba shares mounted using nautilus? gvfs?

then you should be able to find the path to where the share's mounted somewhere in ~/.gvfs (something along those lines)

alternatively, you can enter an fstab entry of your samba share (i remember seeing a really good tutorial around here)

---

### Post by jmauld on 2009-10-10
> **renkinjutsu said:**
> Are these samba shares mounted using nautilus? gvfs?

then you should be able to find the path to where the share's mounted somewhere in ~/.gvfs (something along those lines)

alternatively, you can enter an fstab entry of your samba share (i remember seeing a really good tutorial around here)

Thank you, the dir. link was under .gvfs.  I'll look for that tutorial on adding the samba share to fstab.  I assume that will make it connect automatically on startup?

---

