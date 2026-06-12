---
title: "Gnome &quot;server connections&quot; (gnome-vfs) path..?"
date: 2006-06-11
forum: General Help
---

### Post by giuliastro on 2006-06-11
Hello,
I really like gnome feature to be able to mount ftp / ssh servers on the desktop. But what is the path to them if I want to access them using a shell? I see the icon/folder on the desktop, but cd'ing to the home/Desktop path I can't see anything.. Thanks in advance.

---

### Post by Ivan Matveich on 2006-06-11
Not possible: the kernel knows nothing about gnome's "mounts." (Unix is a stupid operating system.) One workaround: use nfs.

---

