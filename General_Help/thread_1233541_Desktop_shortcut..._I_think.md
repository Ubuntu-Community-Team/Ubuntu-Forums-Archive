---
title: "Desktop shortcut... I think?"
date: 2009-08-06
forum: General Help
---

### Post by paul_be on 2009-08-06
Hey I was looking to write a script to make shortcuts/links to default folders in the home directory to the desktop.  ie Documents Videos etc...  I was wondering what command I should use.  Is **ln** the proper command for the job?

Thanks
Paul B

---

### Post by SoftwareExplorer on 2009-08-06
```
ln -s
``` would make symbolic links
```
ln
``` would make hard links.

Symbolic links point to a folder and it appears to be in two places. They can span across volumes and programs treat them like a normal folder. Quite handy. If the origanal folder is deleted, they no longer work.
Hard links have to be on the same volume. They seem like a symbolic link at first, but if you delete the original folder, they take over the data, so no space would be freed, instead it would be like the data saved where the link was.

---

### Post by paul_be on 2009-08-06
Thank you the symbolic link worked just perfectly, I was try to do a hard link which I was restricted from doing.

---

### Post by SoftwareExplorer on 2009-08-06
Your welcome. I've done some pretty wild things with symbolic links. Like multiple owners of a folder.

---

