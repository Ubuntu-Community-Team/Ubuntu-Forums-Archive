---
title: "How to Change Sound Theme in Ubuntu 11.10?"
date: 2011-10-20
forum: General Help
---

### Post by linuxinstalledfromhdd on 2011-10-20
Hi there. I'm trying to change the sound theme from the default to

sudo apt-get install ubuntustudio-sounds

and then I run

gnome-volume-control

But when I run gnome-volume-control nothing happens.  It says it isn't installed. 
When I try to install it, it says it is not available. 

How do I change the sound theme to ubuntustudio-sounds???

It worked like this in Ubuntu 11.04, and the theme installs fine, but I can't change the configuration settings for the sound theme... hmmmmmm...  Isn't that funny??:p

---

### Post by linuxinstalledfromhdd on 2011-10-21
BUMP:popcorn:

---

### Post by brainpower on 2011-10-30
open gconf-editor,
go to "/desktop/gnome/sound/" and change "theme_name" to your desired theme,
eg. "ubuntustudio"...

---

### Post by jimmydean886-2 on 2011-12-04
Alright. There's one problem with the first answer given here.

Gconf-Editor is now depricated, and no longer works for that kind of thing. Compiz and some other things still use it, but GNOME uses dconf-editor.

install it using 
```
 sudo apt-get install dconf-tools 
```
Then try to launch the dconf editor either by typing
```
dconf-editor
```
in the command line, or just searching it using the Dash.

Navigate in the sidebar to /org/gnome/desktop/sound and then look in the main window for an entry called "theme name"

change this to whatever sound theme you like.

---

