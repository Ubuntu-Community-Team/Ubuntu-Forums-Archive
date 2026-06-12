---
title: "Help with Jaunty random login fails."
date: 2010-01-16
forum: General Help
---

### Post by smoosh on 2010-01-16
Hey, running Jaunty, and recently, i believe after messing with Startupmanager, I get random login failures. Sometimes, it shows my nautilus wallpaper, then goes to the login screen, sometimes it shows my nautilus wallpaper, then loads my compiz wallpaper like normal, but has a window that says "your session lasted less than 10 seconds...", sometimes it loads everything normally, sometimes it loads my normal desktop, only the panel is bare, and I can only start certain program like gimp and ardour but not any terminal or filebrowser type programs.

I have since removed startupmanager and usplash altogether (usplash never worked right after startupmanager got it's ugly paws on it), but still, the login goofiness continues. There are no strange errors during grub's verbose boot that I can see, everything loads normally. During logout, there is one strange line that says something about removing /org/freedesktop/hal/ and a uuid of some kind (I think). It blinks by really fast, so I haven't documented it well.

Once in 15 boots of so, when everything loads normally, my computer functions flawlessly! Other than that, it is a cycle of confusion and completely random unexplainable errors.

Running grub2 if that helps. 

Anybody ever have this happen, and any ideas on what I can do to fix it?

Thanks in advance!

L

---

### Post by smoosh on 2010-01-17
OK, anybody else having crazy login issues like this: 


go to: home/{user}/.config/

and remove the folder:

gnome-session

-------------------------------------------------

This happened to me because a file in that folder was telling the session manager to start a program that I removed, resulting in an I/O error, somehow.

---

