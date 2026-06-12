---
title: "Editing Gnome-do docky launchers"
date: 2009-06-27
forum: General Help
---

### Post by NSDragon on 2009-06-27
Hello all. I've been trying to use the docky interface of Gnome-do (0.8.1.3) for a while under Xfce, and while it does run fine and all, I've found a minor snag.

Under Gnome, one can drag and drop any launcher from, say, the gnome-panel onto Gnome-do and add it this way to the dock interface. Under Xfce (and I suspect KDE as well, but I haven't tried it) I can't do this. Now I know I can do a search and add items from there, but this doesn't let you customize the launchers. To get custom launchers I'd normally add them to gnome-panel, edit them there, and drag them onto the dock from there. But this drag-and-drop doesn't work in Xfce, and thus I can't really add or customize them in any way.

I'm wondering if anyone has found a way to customize these launchers, or a workaround or anything. I've searched for any .desktop files that gnome-do might be using, hoping that I could edit those at least, but I haven't found anything yet.

---

### Post by DBO on 2009-06-28
You can make a launcher on your desktop (I think xfce will let you do this) and then drag from there.

---

### Post by NSDragon on 2009-07-10
Didn't think of that, but it sounds like it might work.

I did find the launchers, however. Or at least some of them: in ~/.local/share/gnome-do/ItemsService_DesktopFiles/ I edited a couple of them and the changes were indeed reflected in the dock

---

