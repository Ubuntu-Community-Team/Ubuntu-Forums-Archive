---
title: "KDE and Gnome"
date: 2006-02-16
forum: General Help
---

### Post by Typhoonsg1 on 2006-02-16
Hi all
Could someone tell me how i install KDE along the side of grub i have just dowloaded KDE from there site :)

---

### Post by ajgreeny on 2006-02-16
Not sure what you mean by "along the side of grub" or why you downloaded from the KDE site.  The easiest way is to use synaptic and install the parts you need, kdebase, kdebase-bin, and kdebase-data, I think are the major 3 needed, but synaptic will work out any dependencies for you.
Alternatively download "kubuntu-desktop" with its dependencies.
After installing when you next bootup if you go to the session menu on the login page you will get the choice of desktop to use.

---

### Post by bonzodog on 2006-02-16
you don't need to install KDE seperately. 
Just issue this command:
```
sudo apt-get install kubuntu-desktop
```
This will download and install ALL needed packages for KDE. Then when you log out of gdm, go to the 'sessions' menu and select 'KDE' before you enter your username and password.

---

