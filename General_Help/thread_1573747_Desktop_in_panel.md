---
title: "Desktop in panel"
date: 2010-09-13
forum: General Help
---

### Post by hotstepperk on 2010-09-13
Is there anyway to have like a desktop icon in the panel, that like shows all the items on the desktop but leaves the background clear, similar to how it is on windows? I keep creating new folders and i hate it when my desktop gets full.. any help will be highly appreciated.

---

### Post by kerry_s on 2010-09-13
sounds like you need to organize & bookmark.
or
you could even use several drawer's & drop folders in them.
or
awn & cairo dock can do stacks if you want to use a dock.

---

### Post by jquis8411 on 2010-09-13
The drawers are the greatest thing ever. Definately try them out

---

### Post by hotstepperk on 2010-09-14
> **kerry_s said:**
> sounds like you need to organize & bookmark.
or
you could even use several drawer's & drop folders in them.
or
awn & cairo dock can do stacks if you want to use a dock.

Close, but something like this, that will hide the icons so I can just see the background/wallpaper and click on the tab to view whats on the desktop. maybe drawers do that, but I dont know how to add locations to the drawer.

---

### Post by kerry_s on 2010-09-14
> **hotstepperk said:**
> Close, but something like this, that will hide the icons so I can just see the background/wallpaper and click on the tab to view whats on the desktop. maybe drawers do that, but I dont know how to add locations to the drawer.

hmm, you can use gconftool-2 to create a script to toggle it on or off.

create a launcher with this command:
```
gconftool-2 --toggle /apps/nautilus/preferences/show_desktop
```

you can create a nautilus script if you want to put it in the right click.

---

### Post by kerry_s on 2010-09-14
> **JayLeenfl said:**
> Hi everyone here.I am so glad to come in here,good to see you all.

well hello there, welcome to the forums.

---

### Post by hotstepperk on 2010-09-14
> **kerry_s said:**
> hmm, you can use gconftool-2 to create a script to toggle it on or off.

create a launcher with this command:
```
gconftool-2 --toggle /apps/nautilus/preferences/show_desktop
```

you can create a nautilus script if you want to put it in the right click.

Pretty nifty, thanks. Problem with that is that now I cant interact with the background :(

---

### Post by kerry_s on 2010-09-14
> **hotstepperk said:**
> Pretty nifty, thanks. Problem with that is that now I cant interact with the background :(

:lolflag: why would you need to, with the icons off?
turn the icons on, do your thing, turn back off, can't get much easier.

---

