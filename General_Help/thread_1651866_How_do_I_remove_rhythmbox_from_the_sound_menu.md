---
title: "How do I remove rhythmbox from the sound menu?"
date: 2010-12-23
forum: General Help
---

### Post by deancasino on 2010-12-23
How do I remove Rhythmbox from the sound menu? Also, I wish for  Rhythmbox to close when the "X" is clicked, can I do these things?

---

### Post by garolou on 2010-12-23
You can configure your menu by clicking on...
System -> Preferences -> Main Menu

as for shutting rhythmbox down completely, instead of hiding it, use CTRL-Q as a shortcut,
or click on the panel Icon and choose Quit... I know, 2 clicks instead of one.

---

### Post by Mgiacchetti on 2011-01-15
> **garolou said:**
> 
System -> Preferences -> Main Menu

That isn't the Sound Menu, that's the system menu, I believe OP is referring to the menu displayed when you click the Sound Icon.

I would also like to know how to remove programs from this area.

---

### Post by unc0nn3ct3d on 2011-03-03
edit ~/.cache/indicators/sound/familiar-players-db.keyfile and remove the reference to Rhythmbox

restart gnome-panel with killall -9 gnome-panel

Viola!

---

### Post by eldonkr on 2011-05-08
> **unc0nn3ct3d said:**
> edit ~/.cache/indicators/sound/familiar-players-db.keyfile and remove the reference to Rhythmbox

restart gnome-panel with killall -9 gnome-panel

Viola!

How is this done in Natty? I didn't find a /sound/ in /.cache.

---

### Post by carlo.bottai on 2011-05-20
> **eldonkr said:**
> How is this done in Natty? I didn't find a /sound/ in /.cache.

I have the same problem. :(

---

### Post by afrodeity on 2011-06-26
I also need to know, this is irritating. 11:04, how?

---

### Post by afrodeity on 2011-06-26
No hack now it seems, you need an editor. Install dconf-tools and use dconf-editor to edit the menu. apps >indicators >sound >interested-media-players

as in this [example]("http://askubuntu.com/questions/48218/banshee-is-still-in-the-sound-menu-after-unistalling")

---

### Post by huggs on 2011-09-28
Here's how to permanently solve this problem.
Look in ~/.local/share/applications for a Rhytmbox desktop file to delete.
There should be two of them, with slightly different names.
Delete both. No more Rhythmbox in sound menu :-)

---

