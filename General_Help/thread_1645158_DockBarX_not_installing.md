---
title: "DockBarX not installing?"
date: 2010-12-14
forum: General Help
---

### Post by Cam! on 2010-12-14
I installed DockBarX via the PPA on OMG Ubuntu. However, when following instructions, the only thing I can access is the preferences for the app, and not the app itself. What's up with that?

---

### Post by Verbeck on 2010-12-14
i think its right click the bottom panel (or top)>add to panel>dockbarx applet

---

### Post by bjnueva8623 on 2010-12-25
I have the same problem. I also installed DockBarX from OMGUbuntu, then through the Synaptic Package Manager. Both claimed to have installed successfully, but the applet is simply missing from the "add to panel" list.

---

### Post by bjnueva8623 on 2010-12-25
Apparently, the **Global Menu Panel** applet is preventing DockBarX from appearing on the Add To Panel list. Remove it in case you have it installed.

---

### Post by karthick87 on 2010-12-25
You have to add the applet to your panel..

[IMG]http://imgur.com/Apbh8.png[/IMG]

---

### Post by M7S on 2010-12-25
DockbarX has had some problems with global menu in the past but I thought those disappeared a long time ago. I use both DockbarX and global menu on my netbook.

If DockbarX doesn't show up in the list after installation the first you should try is to restart the gnome panel.

```
killall gnome-panel
```

---

