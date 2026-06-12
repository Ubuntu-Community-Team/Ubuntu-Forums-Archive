---
title: "Nested NFS mounts"
date: 2009-08-05
forum: General Help
---

### Post by TigerCR1200 on 2009-08-05
I want to mount to NFS shares. However the file structure is as so:

/Downloads and
/Downloads/Music

I want to mount them in my home directory as 
/home/user/Downloads
/home/user/Music

Will this cause any issue or would it be better to make two shares on the NFS server one for Downloads and one for Music?

---

### Post by TigerCR1200 on 2009-08-07
In case someone comes searching at a later time for this answer, I have mounted the nested folders through fstab and have not noticed a problem yet.

---

### Post by Jose Catre-Vandis on 2009-08-07
You could always just mount /Downloads and then symlink on your client PC to the /Downloads/Music folder in your mount? This would save a share problem.

This is a snip in Thunar, just right click on Music and Send To SidePane, but I guess you can do similar in other File Managers

---

