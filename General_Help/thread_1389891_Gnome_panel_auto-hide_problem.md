---
title: "Gnome panel auto-hide problem"
date: 2010-01-24
forum: General Help
---

### Post by l3lackfable on 2010-01-24
First off, I'm using Ubuntu 9.10.
Ok the Top panel, I right clicked and went to properties and checked "Auto-Hide" and now it's permanently hidden. and I can't get it back... 

Any help would be much appreciated, thx.

---

### Post by howefield on 2010-01-25
Try pressing the Alt + F2 and in the run box type,

```
gconf-editor
```

Navigate to apps > panel > toplevels > top_panel_screen0 and uncheck the box next to auto_hide.

Does that do it ?

You might have to look at some of the other options.

If this doesn't work, you can put the panels back to default by deleting the configuration folder in /home. But doing that might be a bit of a sledgehammer to crack a nut ;)

---

### Post by bennyhash on 2010-01-25
I got a similar kinda problem with my panels.

I wanted to put them both over to the left-hand side, and now they've frozen. 

I can't left-click to edit properties and I can only open t'interweb by pressing F1 and getting the help thing up.

---

### Post by l3lackfable on 2010-01-25
ah, yeah, that did it. thanks a lot. For a second there I though I would have to reinstall ubuntu...

---

### Post by howefield on 2010-01-25
> **bennyhash said:**
> I can't left-click to edit properties and I can only open t'interweb by pressing F1 and getting the help thing up.

Maybe this is a typo., but you need to right click to edit the panel properties.

Or to reset to default. Open a terminal (Applications > Accessories > Terminal) and type the following command.

```
rm -r ~/.gconf/apps/panel
```

This will remove the configuration data for your panels, which will be rebuilt next time you log in to gnome. Log out of your session and back in.

If you can't use the menus to open your terminal, press the Alt + F2 keys together and type

```
gnome-terminal
```

PS. You could rename or move the folder instead of removing if you wanted to hold on to it for any reason.

---

### Post by avl555 on 2011-01-10
> **l3lackfable said:**
> ah, yeah, that did it. thanks a lot. For a second there I though I would have to reinstall ubuntu...

You don't have to reinstall Ubuntu for such simple things. This is something where you don't have to be root (admin) for. And then it is very, véry unlikely that you break something that needs reinstalling (it shouldn't be possible).
And generally, big problems are also solvable.

---

