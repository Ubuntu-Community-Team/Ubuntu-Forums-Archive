---
title: "How to change program icon."
date: 2009-09-25
forum: General Help
---

### Post by Missing_Number on 2009-09-25
How do change the icon for a program?  I want it changed everywhere, including the bar at the bottom and at the left-hand corner of the screen on the window, not just the menu icon. (I know how to do that.)

---

### Post by Missing_Number on 2009-09-25
Update: I've read some other posts on this board relating to this, but none of them helped me.  Sorry if this sounds dumb.

---

### Post by wojox on 2009-09-25
Have you looked in  /usr/share/pixmaps ? 

That's where their stored.

---

### Post by Missing_Number on 2009-09-25
Yes.  When I've replaced them, they eventually become "lost" later.  Even then when I do manage to replace them using sudo nautilus, it still displays the old icon, even after I type "killall gnome-panel".

---

### Post by CatKiller on 2009-09-25
> **Missing_Number said:**
> How do change the icon for a program?  I want it changed everywhere

It's (icon) theme-dependent. You'd need to change the (appropriately named) icon for each size for the icon theme that you're using. Icon theme icons are stored in /usr/share/icons/*themename* (for system-wide themes) or ~/.icons/*themename* (for per-user themes).

---

### Post by RedRat on 2009-09-25
This is an interesting question. Where do the program icons come from. In Windows they are usually installed within one of the dlls or even in the exe program. In Windows you can usually open either of these files and see the icon choices. In my version of Ubuntu, 8.04, I do not find any icons in pixmaps. 

However in Linux I have yet to find where the actual program icon is stored. Yes, in usr/share/icons there is a slew of icons but these are all that you can replace existing icons. 

I am using AWN tool bar and sometimes the icons stick and sometimes they do not. Haven't figured out why this happens. Any ideas.

---

### Post by VCoolio on 2009-09-25
You could also check the launcher and see what icon is specified. The launcher can e.g. be in /usr/share/applications, /usr/local/share/applications or ~/.local/share/applications; open in text editor and read the "Icon=" line; if it's a path, it has it's own icons installed; if it's just a filename, it is included in your icon theme. If you configure it to the icon you want, it should also change in your panel (after restarting the panel), gnome-do etc. Check the user folder that I mentioned first: that overrules the system folders.

---

