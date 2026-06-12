---
title: "Configuring Autorun for Removable Media"
date: 2011-03-28
forum: General Help
---

### Post by Rocket J Squirrel on 2011-03-28
(Ubuntu 10.10, Unity desktop)

How can I configure Ubuntu to launch gtkpod when I connect my iPod? It's currently launching Rhythmbox. 

I can't find anything about removable media in Unity's Toolbar > Applications 

They musta hidden it.

---

### Post by mc4man on 2011-03-29
It's in File Mangement > Media > Music player
(file management is not enabled in your System > Preferences menu by default, either enable it in edit menus (alacarte) or nautilus > edit > preferences
or go in a terminal
nautilus-file-management-properties

Expand the dropdown, pick 'Open with other application'. If gtkpod isn't in the list then choose 'use a custom command', enter gtkpod

---

### Post by Rocket J Squirrel on 2011-03-29
Thank you.

nautilus > edit > preferences did the trick.

---

