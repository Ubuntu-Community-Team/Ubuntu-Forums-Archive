---
title: "gdesklets not working"
date: 2006-03-06
forum: General Help
---

### Post by WarAngel on 2006-03-06
gDesklets stopped working after I tried to use Multitail. I changed the font size of the text display, and now it refuses to do anything. When the shell loads, it displays blank (see picture). Any clues?

[http://i8.photobucket.com/albums/a9/warangel999/gdesklet-shell.png](http://i8.photobucket.com/albums/a9/warangel999/gdesklet-shell.png)

---

### Post by ComplexNumber on 2006-03-06
whats multitail?

---

### Post by beck24 on 2006-03-06
I had this problem just this morning, they stopped working randomly and I got the same hanging on the shell.

Just use synaptic to uninstall gdesklets completely, and (this is important) you must delete the ~/.gdesklets directory (otherwise the problem remains if you reinstall).

Once it's all off you can reinstall and it should work.
There's probably a more elegant solution, but this worked for me.

---

### Post by ComplexNumber on 2006-03-07
guys, don't forget that the gdesklet daemon has to be restarted each time you log in. to do this automatically, find 'sessions' in either the menu or the gnome control centre. add the following to 'sessions' - 'gesklets start'

---

