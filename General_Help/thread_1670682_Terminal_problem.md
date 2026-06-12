---
title: "Terminal problem"
date: 2011-01-19
forum: General Help
---

### Post by DiabloShell on 2011-01-19
Hi,i wanted to change the size of the terminal like so whenever i open it up it will be fullscreen so i went at preferences and changed the size thing at the left (i think it was columns) to 700.Now whenever i open up a terminal the whole screen freezes and it logs me out.Any help appreaciated.
really sorry for the double posting i have no idea how i did that

---

### Post by Hippytaff on 2011-01-19
You can do CTRL+ALT+F1 to open tty1 which is a terminal, in full screen...just press F7 to return to the ubuntu desktop

---

### Post by zealibib slaughter on 2011-01-19
You may need to edit or replace the default profile xml file with one that works.  Its located at ~/.gconf/apps/gnome-terminal/profiles. I don't know if that will fix the problem but it might.

---

### Post by zealibib slaughter on 2011-01-19
You may need to edit or replace the default profile xml file with one that works.  Its located at ~/.gconf/apps/gnome-terminal/profiles. I don't know if that will fix the problem but it might.  You can change the settings by pressing alt+f2 and typing gconf-editor then goto apps > gnome-terminal.  I just remembered this tool.

---

### Post by WorMzy on 2011-01-19
Open gconf-editor (Alt+F2, gconf-editor, run) and browse to /apps/gnome-terminal/profiles/Default, look for the "default_size_columns" and set it to something a little less extreme, like 80. ;)

Since it works in columns and rows, and not pixels, 700 would translate to something like 2800px+, depending on your font and font-size.

---

### Post by DiabloShell on 2011-01-19
Thanks a lot guys.It's ok now

---

