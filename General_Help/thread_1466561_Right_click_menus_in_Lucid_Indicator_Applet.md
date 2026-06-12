---
title: "Right click menus in Lucid Indicator Applet?"
date: 2010-04-30
forum: General Help
---

### Post by magnus0 on 2010-04-30
Why are there no menus on the icons? For example when I right click Rhythmbox icon, i should see a menu, like in Karmic. Or when I left click Emesene, i want it to show, not display a stupid Show/Hide menu.

Basically what I want is to be able to toggle show/hide with left click, like before. Right now, it only displays a small menu.

I can't figure anything out here -.-

---

### Post by pqwoerituytrueiwoq on 2010-04-30
```
gconftool-2 --set --type Boolean /desktop/gnome/interface/menus_have_icons True
```That do what you want?
if you decide to undo it here is the undo command
```
gconftool-2 --set --type Boolean /desktop/gnome/interface/menus_have_icons False
```EDIT:
reread post 
i really need to quit skimming:lolflag:
------------------------------------------------------------------------------------------
Have you tried left clicking it?

---

### Post by magnus0 on 2010-04-30
> **pqwoerituytrueiwoq said:**
> ```
gconftool-2 --set --type Boolean /desktop/gnome/interface/menus_have_icons True
```
That do what you want?
if you decide to undo it here is the undo command
```
gconftool-2 --set --type Boolean  /desktop/gnome/interface/menus_have_icons False
```
<div id="alert" style="position: fixed; left: 0px; top: 0px; z-index: 99999; color: white; background-color: black; -moz-border-radius-bottomright: 5px;">Re-enable Sharks</div>[/CODE]

no.

I'm talking about the indicator applet, i cannot focus the application when left clicking. it just i displays a stupid menu.

---

### Post by pqwoerituytrueiwoq on 2010-04-30
edited previous post

---

### Post by psyced on 2010-05-01
I'm also quite ticked off by this.
Why did they even change it? It's now showing the menu options for the indicator applet instead of the menus for application icons.

---

### Post by Ryan Dwyer on 2010-05-01
Consistency is one reason. With a bunch of different icons it's difficult to remember whether to left click or right click them to get the menu, so they've made it consistent.

The left click hide on some applications has been removed as well, because that's not how the indicator applet/notification area is intended to operate. It's there to indicate and notify. Hiding programs should be done by placing them on a different virtual desktop.

---

### Post by pihbar on 2010-05-01
They've made it consistent for the three supported applications. I oppose indicator-applet.

---

### Post by geoffm on 2010-09-18
> **pihbar said:**
> They've made it consistent for the three supported applications. I oppose indicator-applet.

I second that.

---

