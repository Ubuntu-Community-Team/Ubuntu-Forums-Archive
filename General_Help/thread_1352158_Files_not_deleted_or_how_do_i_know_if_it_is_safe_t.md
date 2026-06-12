---
title: "Files not deleted? or how do i know if it is safe to delete."
date: 2009-12-11
forum: General Help
---

### Post by aklo on 2009-12-11
So i installed cairo docks the other day and found that i could do without it since the normal menu is good enough for me.  I uninstalled it and while learning new linux command line terminal with "du" i saw that cairo docks still have files in my system.

Question is can i use the rm command safely without accidently deleting my system files? If not are there any specific uninstall command i can use to remove programs CLEANLY?
How do i know which files i can't delete? How are they organized in ubuntu? 

Belows are just some of the files i copied from the command line.

108    ./.config/cairo-dock/themes/MacOSX/launchers
8    ./.config/cairo-dock/themes/MacOSX/plug-ins/dustbin
8    ./.config/cairo-dock/themes/MacOSX/plug-ins/switcher
12    ./.config/cairo-dock/themes/MacOSX/plug-ins/logout/.svn/prop-base
4    ./.config/cairo-dock/themes/MacOSX/plug-ins/logout/.svn/props
4    ./.config/cairo-dock/themes/MacOSX/plug-ins/logout/.svn/tmp/prop-base
4    ./.config/cairo-dock/themes/MacOSX/plug-ins/logout/.svn/tmp/props
4    ./.config/cairo-dock/themes/MacOSX/plug-ins/logout/.svn/tmp/text-base


Upon further searching from the synaptic package manager, i see about 7-8 programs which are installed with names like libcairo2, python-cairo etc. When trying to uninstall them, it prompt me that it might affect my other programs that are using it like art-manager etc. So i'm not sure if i should remove them. 

Help

---

### Post by benj1 on 2009-12-11
those file that you listed are just themes, so its safe to delete them.
in the future if youre using synaptic use 'mark for complete removal' (apt-get use 'purge') that will get rid of all the config files, aswell as the program

with other files when you mark for removal and click apply (in synaptic) you can review whats to be removed.

but be aware, cairo is used for many things, so these libs may well have been installed for something else and thats why they haven't been removed

---

### Post by aklo on 2009-12-11
What about the names of the app?

How do i know what names are they? for example cairo docks. 

apt-get purge cairo docks
or
apt-get purge cairo_docks

or whatever

---

### Post by arubislander on 2009-12-11
> **aklo said:**
> What about the names of the app?

How do i know what names are they? for example cairo docks. 

apt-get purge cairo docks
or
apt-get purge cairo_docks

or whatever

Well, what you use as apt-get arguments are not the app names but the package names. They will never contains spaces, so:
```
apt-get purge cairo docks
```
would try to purge the packages cairo and docks.

You never know how a packages is named unless you search for it in synaptic. But you can also use tab to complete the name so:
```
apt-get install cairo-[TAB]
```
in Karmic would give you:
```
cairo-5c                         cairo-clock-hildon               cairo-dock-core                  cairo-dock-dev                   cairo-dock-plug-ins-data
cairo-clock                      cairo-dock                       cairo-dock-data                  cairo-dock-plug-ins              cairo-dock-plug-ins-integration
```

---

### Post by benj1 on 2009-12-11
im not sure you would be able to use apt-get purge in this instance because its already been removed, although you could reinstall and purge then. i was just pointing it out for future reference.

---

### Post by bodhi.zazen on 2009-12-11
depends on where those files are located.

purge will purge system files in sat /etc , but not . files in your home directory.

If the files are in your home directory you may delete them. If they are system files, re-install then purge ;)

---

### Post by aklo on 2009-12-11
Many thanks ! and it gets clearer now. I just installed inkscape with the commands and feels good to do it on a CLI.

Problem solved.

---

