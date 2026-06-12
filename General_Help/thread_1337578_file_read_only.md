---
title: "file read only"
date: 2009-11-25
forum: General Help
---

### Post by Static42 on 2009-11-25
I have a file in my /opt/lampp/htdocs folder that I would like to edit. So I open up the gedit text editor and make changes, but I can't save the file because the file is read only. How do I give myself permissions to save the file?

---

### Post by raktarok on 2009-11-25
Open it with root privileges:
gksudo gedit /opt/lampp/htdocs/<filename>

---

