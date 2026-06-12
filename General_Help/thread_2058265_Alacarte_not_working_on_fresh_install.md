---
title: "Alacarte not working on fresh install"
date: 2012-09-15
forum: General Help
---

### Post by sienile on 2012-09-15
I just reinstalled due to a window manager crash and now _**alacarte** will not edit my menus_.

I've attempted to fix the problem by reinstalling alacarte and all of its dependancies, even installing the recommended but not required packages; but this did nothing to fix my problem.

I've ran it with gksu to make sure it's functioning as root, but this made no change.

Any ideas what could be causing this? Is there a way I can edit my menus manually until I get this fixed?

---

### Post by sienile on 2012-09-15
I noticed a few other errors in other programs being unable to write to their config files, so I went to reinstall. I noticed my install disk had some smudges on it, so I cleaned it before this install.

Reinstalling fixed errors in other programs (again :evil:), but alacarte is still not working. ](*,)

---

### Post by sienile on 2012-09-15
After some poking around, I've found where the alacarte config files are.

```
/home/user/.config/menus/applications.menu
/home/user/.local/share/applications
/home/user/.local/share/desktop-directories
```

Oddly enough, alacarte is editing the files properly. But for some reason the system is not reflecting the changes. What gives?! How do I make the system recognize the alacarte files???

---

### Post by sienile on 2012-09-15
Yet another one of my problems solved by me. :P

**/etc/xdg/menus/applications.menu** for some reason contained the below lines.
```
  <!-- The Debian menu -->
  <Menu>
    <Name>Debian</Name>
    <MergeFile>debian-menu.menu</MergeFile>
    <Directory>Debian.directory</Directory>
  </Menu>
```
Once those lines where deleted all my changes magicly appeared. Now if I could only find out what screwy app added those lines in the first place...

---

### Post by davidmcq on 2012-11-09
Alacarte was failing to update with new applications installed from source. The standard unity interface (grrrrr.....) didn't recognise the new application, and Alacarte (aka "Main Menu") wouldn't update. It turns out that you need a package called gnome-panel:

sudo apt-get install gnome-panel

After that you can invoke either "Alacarte" or "Main Menu" from the meta (Windows) key and add your application.

---

### Post by Mike Green9 on 2013-01-16
Thanks DAVIDMCQ - your fix worked like a charm :D


M.....

---

