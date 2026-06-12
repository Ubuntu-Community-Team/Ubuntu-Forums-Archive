---
title: "Control-c, control-v stopped working"
date: 2011-01-19
forum: General Help
---

### Post by MichaelGld on 2011-01-19
I don't know how this happened, but my keyboard copy and paste functions have stopped working. Oddly enough, I discovered that I can only copy and paste by using the third mouse button. Pressing down on the scroll wheel after highlighting text copies the text, pressing it again pastes it  Ican still use the Edit-copy and Edit-paste menu functions.

I'm sure it has something to do with all the tinkering I have been doing with my desktop. I have been experimenting with CompizConfig and Cairo dock, changing my themes and things of this nature. 

Ububtu 10.04.1
kernel 2.6.32-27 generic

---

### Post by sum1nil on 2011-01-19
I wonder if this is a windows manager problem ie compiz it would seem.

You can change your default window manager to another say gnome-wm in gconf-editor at 
/desktop/gnome/session/required_components/windowmanager

Good luck!

---

### Post by MichaelGld on 2011-01-20
mods please delete

---

### Post by MichaelGld on 2011-01-20
mods, please delete

---

### Post by MichaelGld on 2011-01-20
mods please delete

---

### Post by MichaelGld on 2011-01-20
mods please delete, overpost

---

### Post by MichaelGld on 2011-01-20
> **sum1nil said:**
> I wonder if this is a windows manager problem ie compiz it would seem.

You can change your default window manager to another say gnome-wm in gconf-editor at 
/desktop/gnome/session/required_components/windowmanager

Good luck!

I found the setting in the gconf editor, and it is already set to gnome-wm.  What now?

Thanks.

---

### Post by MichaelGld on 2011-01-21
> **MichaelGld said:**
> I found the setting in the gconf editor, and it is already set to gnome-wm.  What now?

Thanks.

After doing some more research, I found it was indeed a Compiz conflict. It was in some of my key bindings in the CompizConfig Manager regarding the cube rotation. I reset any of them that were using the Control key, and like magic, my copy and paste functions returned to normal.

---

