---
title: "Where are the theme graphics for window controls stored?"
date: 2010-05-01
forum: General Help
---

### Post by dwasifar on 2010-05-01
Where are the graphics stored for window controls?  They change with the theme, so they must be part of the theme graphics.  Specifically I'm looking for these:

[IMG]http://www.dwasifar.com/share/theme.png[/IMG]

In Lucid's Ambiance theme, they're little plus and minus boxes.  I prefer the rotating arrows and want to edit the theme to replace them.

---

### Post by dwasifar on 2010-05-22
bump

---

### Post by ankspo71 on 2010-05-22
Hi,
I only have Kubuntu, so I don't have any Ubuntu themes to look though. But I can help you try to located them...

Look in /usr/share/themes/
there you should see all choices of themes.
Each of those folder should have the following folders.

Metacity = window borders
Gtk = basically everything else

browse though the Ambiance's (or another theme's) gtk folder for any images that look like those arrows you want. Make a note of the names and locations so you can edit them directly later on or find their settings in the gtkrc file. Then go look for the file called gtkrc and open it. That would be the file for the theme's gtk configuration. Using your text editor (gedit), use the find feature to locate the lines that uses the image's name. Here you can edit the locations to the images it uses (for instance have them use images from another theme. or possibly adjust their sizes)

Once you have that sorted out, you should be able piece together something, either by editing the gtkrc or editing the tiny images it might use.
Hope this gets you started.

---

