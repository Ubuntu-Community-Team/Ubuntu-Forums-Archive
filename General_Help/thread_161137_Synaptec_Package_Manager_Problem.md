---
title: "Synaptec Package Manager Problem***"
date: 2006-04-16
forum: General Help
---

### Post by rtfmviolator on 2006-04-16
When I install programs through Synaptec Package manager they don't load in the menus. I search for the programs and I find some things sometimes, but hardly ever. This is frustrating me to no end. I've installed many, many things but it's as if I did not install anything. SOS!!!!

---

### Post by aysiu on 2006-04-16
Well, two things are at issue.

1. You may need to refresh the Gnome panel. You can do this by pressing Alt-F2 and typing ```
killall gnome-panel
``` That way, newly created menu entries will actually show up.

2. Some programs, depending on what you install, don't create a menu entry, so... you have to create it yourself, or pester the developers of that application to create one.

---

### Post by ncappel1 on 2006-04-16
Some programs wont load themselves automatically into the panel menus, but you can add them there yourself by using Applications-->System tools-->Applications menu editor (or by typing "smeg" into a command line terminal)

Once you're there you can select where you want to put the link to the program. click on "new entry" and type in the information for the program, along with the command for the program. (which is usually the name of the program you downloaded in synaptic"

---

