---
title: "[SOLVED] Possible Bug when Changing Icons"
date: 2006-06-07
forum: General Help
---

### Post by vayde on 2006-06-07
Ive noticed something irritating/ wierd.  When you right click on a launcher->properties->icon: if you try to type in a path to search for icons, it crashes or drops back to the launcher->properties window on every key press.

This is happening to my laptop as well as on a desktop, so it's not just me bumping the touchpad (which happens plenty).

Choosing 'browse' is not always an option, as in my case, the icon I was looking for is in /home/vayde/.icons , and doesn't show up on the browse menu. 

Im not sure if this is a bug, or just my ineptitude, and Im not sure if in this case Im dealing with Gnome, or Nautilus, or Metacity, etc.  If someone can enlighten me as to  where the problem, I can probably direct this to a more specific venue.

---

### Post by johnc4510 on 2006-06-07
Don't know about fixing that problem, but you can do this to make your icon accessable:
Applications>Accessories>Terminal
type in: sudo nautilus and your password
Then use your mouse to navigate to the /usr/share/lpixmaps file and then drag and drop your icon there, and it will be available to use

---

### Post by vayde on 2006-06-07
[QUOTE=johnc4510]Don't know about fixing that problem, but you can do this to make your icon accessable:
Applications>Accessories>Terminal
type in: sudo nautilus and your password
Then use your mouse to navigate to the /usr/share/lpixmaps file and then drag and drop your icon there, and it will be available to use[/QUOTE]

So it IS nautilus that I'm having trouble with?  Thanks.  

I managed to brute force it, it's n not really a problem, but I figure if it is a bug, then someone should know about it.  It definitely wasn't a problem in Breezy

EDIT: Problem went away with the last round of gnome  updates

---

