---
title: "Using terminal to change desktop"
date: 2006-04-02
forum: General Help
---

### Post by ralin on 2006-04-02
Is there a command to change the desktop picture?
also to change it to no picture just a solid color. 

thanks

---

### Post by nanotube on 2006-04-02
well, it's not that easy, unfortunately. (at least assuming you are using gnome). gnome stores its desktop background prefs in gconf (accessible via gconf editor, through Applications>System Tools>Configuration Editor). if you want to do it through commandline, you would have to edit this file:
~/.gconf/desktop/gnome/background/%gconf.xml
and change the "picture_filename" entry. 
so that would probably require writing a little bash script if you want to keep doing that on a regular basis. :) should be easy enough to do, since the line number that needs editing always stays the same, as far as i know.

oh, and if you want to change colors without pictures, you would change the other items, most notably the "primary_color" one.

---

### Post by halitech on 2006-04-02
[QUOTE=ralin]Is there a command to change the desktop picture?
also to change it to no picture just a solid color. 

thanks[/QUOTE]


if you are using gnome, just right click the desktop and select change Desktop Background and you can select no picture, add new pictures to your background list and select what color you want for the background if you don't want a picture.

hth.

---

### Post by ralin on 2006-04-02
[QUOTE=nanotube]well, it's not that easy, unfortunately. (at least assuming you are using gnome). gnome stores its desktop background prefs in gconf (accessible via gconf editor, through Applications>System Tools>Configuration Editor). if you want to do it through commandline, you would have to edit this file:
~/.gconf/desktop/gnome/background/%gconf.xml
and change the "picture_filename" entry. 
so that would probably require writing a little bash script if you want to keep doing that on a regular basis. :) should be easy enough to do, since the line number that needs editing always stays the same, as far as i know.

oh, and if you want to change colors without pictures, you would change the other items, most notably the "primary_color" one.[/QUOTE]


I figured it was going to be soemthing complex like that i will look it up and give it a try because it was going to be in a script anyways.  Thats also why i cant just use the gui utility to change it.  Thanks for the help

---

### Post by nanotube on 2006-04-03
well, have fun. :) feel free to post further in this thread if you need help with the script...

---

### Post by mlalkaka on 2006-04-03
gconf has command-line tools to change configuration entries. That should make it easy (or at least easier to do what you need). Refer to the man pages of gconf* for more information. There are quite a few gconf command-line tools available, it seems, but I think the one you need is either gconfigger or gconftool. Again, the refer to the man pages.

---

### Post by nanotube on 2006-04-03
mlalkaka: good thinking! i didnt know about those. after looking around in man, seems like the relevant tool would be "gconftool-2". great! :)

---

