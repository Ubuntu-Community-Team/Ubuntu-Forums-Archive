---
title: "reinstall gnome"
date: 2006-04-13
forum: General Help
---

### Post by marcwenger on 2006-04-13
I accidentally uninstalled essential files for gnome and now I am unable to access the ui.

How do I, via the command line and an internet connection, reinstall gnome?


Thanks

---

### Post by Mr. Polite on 2006-04-13
From the command line type:

sudo apt-get install ubuntu-desktop

Select 'GDM' as you display manager if it ask.

---

### Post by Ramses de Norre on 2006-04-13
sudo apt-get install -f
sudo apt-get install --reinstall gnome-desktop-environment
If those don't work: can you give some more details about which files you deleted and which error you get.

---

### Post by marcwenger on 2006-04-13
Thank you!  It worked

---

