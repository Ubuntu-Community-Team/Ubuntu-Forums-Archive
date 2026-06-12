---
title: "Can't change default window theme in Gnome 3"
date: 2011-06-08
forum: General Help
---

### Post by mikegioia on 2011-06-08
Hey guys -

I recently went through a desktop crisis after removing unity from 11.04, installing openbox, hating it, and then installing Gnome 3.

What's weird is certain applications like chrome and some other system things appear to use the theme I have (as in, they look nice) but windows like terminal, file browser, and most other applications including the default log in screen all look like windows 95.

[IMG]http://i.imgur.com/YPAKJ.png[/IMG]

you can see the square unstyled buttons. I'm just wondering how to apply a full on system theme to apply to all windows in gnome 3. tweak-gnome didn't look like it could do it, and after running through the themes (redmond, clearlooks, etc) they didn't have any impact on these windows.

thanks for any help you guys might have,
mike

---

### Post by cbowman57 on 2011-06-08
Probably looks that way because your theme either has no gtk-2.0 theme, or a very basic one.  Add one you like or edit your existing one.

---

### Post by mikegioia on 2011-06-09
thanks cbowman57, this thread had what i needed:

[http://ubuntuforums.org/showpost.php...3&postcount=86](http://ubuntuforums.org/showpost.php...3&postcount=86)

i had to unpack that directory into /usr/share/themes and presto, i was able to switch to adwaita.

---

### Post by cbowman57 on 2011-06-09
Ok, good to know you got it working.

---

