---
title: "Problem in installing totem-xine"
date: 2006-02-02
forum: General Help
---

### Post by kenweill on 2006-02-02
I wanted to install totem-xine. 
But I was having a problem with this message(a thumbnail is attached).

Why does the system want to remove ubuntu-desktop in order to install totem-xine?

What will happen if ubuntu-desktop is removed? Should I still get a GUI?

---

### Post by CompShrink on 2006-02-02
Uninstalling Ubuntu-Desktop is fine.

Ubuntu-Desktop is just like a table of contents, it lists (as dependancies) all the software in the basic ubuntu install.

Installing Totem-Xine makes you uninstall Totem-GStreamer. Totem-GStreamer is part of Ubuntu-Desktop's list (of dependancies), so it makes you uninstall Ubuntu-Desktop.

It's perfectly fine and harmless to do.

---

### Post by kenweill on 2006-02-02
[QUOTE=CompShrink]Uninstalling Ubuntu-Desktop is fine.

Ubuntu-Desktop is just like a table of contents, it lists (as dependancies) all the software in the basic ubuntu install.

Installing Totem-Xine makes you uninstall Totem-GStreamer. Totem-GStreamer is part of Ubuntu-Desktop's list (of dependancies), so it makes you uninstall Ubuntu-Desktop.

It's perfectly fine and harmless to do.[/QUOTE]

It works perfectly.
When I installed kubuntu-desktop before, in some other computer, it installed the KDE and Kubuntu.

I thought removing ubuntu-desktop will remove my GNOME GUI. Since I have only GNOME, I was afraid if it will be removed as well.

So, anyway, thanx alot.

---

