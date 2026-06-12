---
title: "how do i remove amarok from sound menu applet?"
date: 2011-01-18
forum: General Help
---

### Post by JuicyCouture on 2011-01-18
i installed amarok which i found not to work very well under gnome - but it still left its little plugin under the sound icon which i would like removed

i searched synaptic and USC for "amarok" but everything seems uninstalled

---

### Post by mc4man on 2011-01-19
If you removed amarok and still see in sound pref.'s then take a look in this file - if an entry for amarok is there then remove, may help
~/.cache/indicators/sound/familiar-players-db.keyfile

---

### Post by JuicyCouture on 2011-01-19
> **mc4man said:**
> If you removed amarok and still see in sound pref.'s then take a look in this file - if an entry for amarok is there then remove, may help
~/.cache/indicators/sound/familiar-players-db.keyfile


ahuh and how do i get into the .cache folder?

---

### Post by mc4man on 2011-01-19
> how do i get into the .cache folder?
among several ways - 
home folder > view > show hidden files (or Ctrl+h

---

### Post by afrodeity on 2011-06-26
there is no sound folder in .cache/indicators on Natty. Install dconf-tools and use dconf-editor to edit the menu. apps >indicators >sound >interested-media-players

as in this [example]("http://askubuntu.com/questions/48218/banshee-is-still-in-the-sound-menu-after-unistalling")

---

