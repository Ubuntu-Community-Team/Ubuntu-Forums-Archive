---
title: "Home icon on panel"
date: 2006-04-18
forum: General Help
---

### Post by Hoffmann on 2006-04-18
Hello:

How can I add the home directory on the GNOME panel. I mean I would like just click on the home icon on the panel in order to access my home directory, instead of Places->Home Folder.

Thanks,
Hoffmann

---

### Post by DeusEx on 2006-04-18
Try to add a Custom Application Launcher of type Link with the Add to Panel menu

---

### Post by Hoffmann on 2006-04-18
[QUOTE=DeusEx]Try to add a Custom Application Launcher of type Link with the Add to Panel menu[/QUOTE]

I know how to do that, and I have done it for several applications. However, in the case of a directory (such as home), how would be the command?

Hoffmann

---

### Post by henryk69 on 2006-04-18
You can have the "Computer", "Home Folder", "Trash" etc icons. Just run **gconf-editor** and go to apps->nautilus->desktop. There you can choose which  icons will be visible on your desktop

---

### Post by nanotube on 2006-04-18
if you just launch "nautilus" without any arguments, it will open up a file browser to your home folder. :)

if you want to open some other folder, just open up "nautilus /path/you/want"

have fun. :)

---

### Post by Hoffmann on 2006-04-18
[QUOTE=nanotube]if you just launch "nautilus" without any arguments, it will open up a file browser to your home folder. :)

if you want to open some other folder, just open up "nautilus /path/you/want"

have fun. :)[/QUOTE]

Hi nanotube,

It worked.

Many thanks!
Hoffmann:-D

---

### Post by Hoffmann on 2006-04-18
[QUOTE=henryk69]You can have the "Computer", "Home Folder", "Trash" etc icons. Just run **gconf-editor** and go to apps->nautilus->desktop. There you can choose which  icons will be visible on your desktop[/QUOTE]


Hey henryk69,

That was a nice hint too.

Thanks!

---

### Post by IYY on 2006-04-18
You can just drag it to the panel from the places menu ;)

---

### Post by chrsjav on 2006-04-18
I was always going to my home folder until i made my home folder my desktop using gconf-editor.  It makes the desktop the starting place for any file navigation actions.  When a file downloads, it's sent to the desktop, right next to my Audio, Video, Documents, etc folders, so it's much easier stay atop of unorganized clutter.  I launch programs from the panel, so there was no point in using my desktop as a subfolder within home.

Just a thought.

---

### Post by chrsjav on 2006-04-18
I'm also really interested in how to make new panel icons.  Why isn't there a option to have *icons* for Applications, Places, System, instead of *words*?  The all-in-one menu is not a good replacement; it is too much menu navigation.

Those of us without much screen resolution (i.e laptop users) should be able to make due with only one horizontal panel, but right now one panel is too crowded to fit the standard word menu plus the tray, date, current apps, etc.  Why do I want less panels?  With the standard top panel, plus the standard Firefox menu including the bookmarks toolbar and tabs, the top 20-25% of my screen is just menus. :(

---

