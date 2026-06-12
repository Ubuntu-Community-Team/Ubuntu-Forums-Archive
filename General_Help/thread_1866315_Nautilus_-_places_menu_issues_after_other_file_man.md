---
title: "Nautilus - places menu issues after other file managers installed"
date: 2011-10-21
forum: General Help
---

### Post by james_mcl on 2011-10-21
I've just installed XFCE and LXDE to try out; however I'm still using Gnome 2.32 for the time being.

After the installations, when I first tried to use the Places menu again in Gnome, I was told I needed to choose a default file manager (Thunar and whatever LXDE uses now being installed). I chose Nautilus and thought that would be it.

However, whenever I use the Places menu to open a folder now, when the folder opens, the cursor stays in spinning-ball mode for a long time, and a taskbar entry for "Opening (the folder in question)" hangs around in the taskbar for a while even after the folder is opened.

The problem doesn't apply to folders opened in any other way.

I've uninstalled the Dolphin and XFE file managers, but the problem still persists.

Possibly relevant information: I'm not using any desktop effects.

---

### Post by james_mcl on 2011-10-21
A little more information - when I right-click on a folder and choose "Open With", the list of applications includes "File Manager" twice. (as well as Thunar and Konqueror)

Also, I've looked in ~/.local/share/applications/mimeapps.list but there's no inode/directory entry in there, so that can't be the culprit.

I've gone into /usr/share/applications/mimeinfo.cache and made nautilus-folder-handler.desktop the first entry in inode.directory, then rebooted. This hasn't solved the problem, and unless anyone can suggest something I think I'm going to have to give up.

---

