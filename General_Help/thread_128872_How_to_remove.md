---
title: "How to remove?"
date: 2006-02-12
forum: General Help
---

### Post by Minyaliel on 2006-02-12
How do I remove the gnome and edubuntu desktops?

---

### Post by Protex on 2006-02-12
sudo apt-get remove ubuntu-desktop && sudo apt-get remove edubuntu-desktop

---

### Post by Minyaliel on 2006-02-12
[QUOTE=Protex]sudo apt-get remove ubuntu-desktop && sudo apt-get remove edubuntu-desktop[/QUOTE]

lovely :) thanks a lot.

---

### Post by Adrian on 2006-02-12
[QUOTE=Protex]sudo apt-get remove ubuntu-desktop && sudo apt-get remove edubuntu-desktop[/QUOTE]

That will not work, because they are meta-packages.

To uninstall ubuntu-desktop, check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=96046&highlight=howto](http://www.ubuntuforums.org/showthread.php?t=96046&highlight=howto)

Using **aptitude** instead of **apt-get** for installing/uninstalling meta-packages is really nice since aptitude keeps track of the installed packages (and can remove them again by just doing an **aptitude remove ubuntu-desktop**, for instance).

---

### Post by Protex on 2006-02-12
Aye, my mistake, sorry.

---

