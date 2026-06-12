---
title: "How do I completely remove tomboy and all its associated files"
date: 2010-12-16
forum: General Help
---

### Post by Mickser_52 on 2010-12-16
I used synaptic package manager to remove tomboy notes and marked it for complete removal. But when I typed "locate tomboy" in the terminal window there were over 50 folders or files listed. Is there a single command I can use to remove all these or do they have to be deleted one by one.

Many thanks in advance for replies

---

### Post by qamelian on 2010-12-16
If any of the folders are hidden or reside in hidden folders inside your home folder, they need to be deleted manually.

---

### Post by Mickser_52 on 2010-12-16
Thanks for response. Many of the files are in  hidden folders .tomboy, .local in the home folder but some are not in hidden folders e.g. /usr , /var . 

Would this be typical of deleting packages in Ubuntu or is this an exception?

---

### Post by Krytarik on 2010-12-16
It is safe to remove the folder in your home-directory, but I wouldn't remove files in other locations, e.g. those in the var-dir are holding infos of the package which are displayed by a package manager, e.g. Synaptic.

---

### Post by sharm on 2010-12-16
Tomboy creates several directories and files in your home directory.  They are specified here:

[http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)

---

