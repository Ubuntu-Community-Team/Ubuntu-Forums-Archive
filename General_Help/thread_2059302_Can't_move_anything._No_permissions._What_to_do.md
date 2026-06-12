---
title: "Can't move anything. No permissions. What to do?"
date: 2012-09-17
forum: General Help
---

### Post by 777funk on 2012-09-17
I'm trying to install plugins and half the time I can't do it because I don't have permissions to do so even though I'm the main user on the machine. 

What is the usual best way to get around this?

Looking around a little heres what I did in Terminal but it's not liking it. Not sure why.
> 
sudo mv /home/nick/Desktop/gcode.lang ~/usr/share/gtksourceview-2.0/language-specs/ 

I've also tried this and I couldn't see anything in the file folders (i.e. desktop is empty)
 	Code:
 	gksudo nautilus

---

### Post by f8l_0e on 2012-09-17
What's the exact error message that you're getting when you try the command?

---

### Post by oldos2er on 2012-09-17
The tilde "~" is shorthand for /home/user, if you remove it from the command you typed it should work (assuming /usr/share/gtksourceview-2.0/language-specs/ exists):

```
sudo mv /home/nick/Desktop/gcode.lang /usr/share/gtksourceview-2.0/language-specs/
```

---

### Post by 777funk on 2012-09-17
> **oldos2er said:**
> The tilde "~" is shorthand for /home/user, if you remove it from the command you typed it should work (assuming /usr/share/gtksourceview-2.0/language-specs/ exists):

```
sudo mv /home/nick/Desktop/gcode.lang /usr/share/gtksourceview-2.0/language-specs/
```

Syntax is what it was. Thanks!

Still can't figure out why nothing shows when I open Nautilus.

---

