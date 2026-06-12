---
title: "Accessing Network Mounts via Terminal"
date: 2011-03-19
forum: General Help
---

### Post by MrPaul on 2011-03-19
Is there a way to access remote mount points that were created within the "Places" dropdown or within Nautilus?  I haven't been able to locate a mount point for these.

I know I can create a mount point using fstab that will solve my problem but I was hoping for something using these automount procedures as it's really clean.

I just want a way to access these remote shares via terminal when created within Gnome.

---

### Post by gzarkadas on 2011-03-19
In my system (9.10) user-mounts made with Nautilus can be accessed through ~/.gvfs/ directory. Do a `ls ~/.gvfs' to display your mounts. Then use the paths as usual.

---

