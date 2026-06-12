---
title: "Gnome 3 Windows boarders not present."
date: 2011-10-20
forum: General Help
---

### Post by galacticaboy on 2011-10-20
I installed Gnome Fallback Session and Gnome-Shell (I installed the shell so I could use the Adwaita theme, my graphics card does not support Gnome Shell...) and when I use Fallback session windows boarders are not there. They are when I have a program in a Windowed mode, but when I maximize it, the close, minimize, and maximize buttons are not there, just the menus that say things like "File Options Help etc", why is that?

---

### Post by galacticaboy on 2011-10-22
***bump***

---

### Post by crdlb on 2011-10-22
This probably has something to do with how Ubuntu has patched metacity for unity-2d. In gconf-editor, at /apps/metacity/general, there is a show_maximized_titlebars setting added via a patch. Is that enabled?

---

### Post by galacticaboy on 2011-10-23
The screenshot is what my windows look like under gnome fallback mode, I have already checked that box in Gconf-Editor... why is there no buttons or anything? How do I get them? They are there in Unity but not Gnome Fallback... it does this with all of the themes to, even Adwaita...

---

### Post by galacticaboy on 2011-10-23
***BUMP Again***

---

### Post by crdlb on 2011-10-23
I still think this has something to do with that unity-2d patch. Does restarting metacity while a window is maximzed do anything?

---

### Post by galacticaboy on 2011-10-24
> **crdlb said:**
> I still think this has something to do with that unity-2d patch. Does restarting metacity while a window is maximzed do anything?

Nope nothing at all.

---

