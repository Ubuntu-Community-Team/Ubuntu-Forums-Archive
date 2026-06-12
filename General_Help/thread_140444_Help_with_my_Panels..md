---
title: "Help with my Panels."
date: 2006-03-06
forum: General Help
---

### Post by abyssspecter on 2006-03-06
Recently i noticed my upper panel (show desktop, trash, windows list) was missing. I clicked on my lower panel, and went to new panel. i re-added the 3 apps on it. i then changed the orientation to 'TOP' like it was before, but it didnt reach the top of my screen, as if the original panel was still there. This is an annoyance to me, but otherwise harmless. But, if someone could tell me what to do, id be greatfull.

[http://photobucket.com/albums/v518/AbyssSpecter/?action=view&current=Screenshotthing.png]("http://photobucket.com/albums/v518/AbyssSpecter/?action=view&current=Screenshotthing.png")

Thats my screenshot.

---

### Post by Sutekh on 2006-03-06
Perhaps the panel is there but has been made fully transparent?  What happens if you right-click the space at the top?  Do you get the panel menu?

---

### Post by abyssspecter on 2006-03-06
thats what i thought. When i click there, it gives me the same menu as when i right click the desktop.

---

### Post by Sutekh on 2006-03-06
Well it was a bit of a long shot.  You have a black desktop right?

Maybe you could re-install *gnome-panel*?

---

### Post by abyssspecter on 2006-03-06
its not black, just on the top.

and how would i do that? im a bit of a n00b.

---

### Post by Sutekh on 2006-03-06
Sure.  You know Synaptic?  Open it up and search for *gnome-panel*, then mark it for re-installation (should be there) and click Apply.  

I'd do this *myself* first to check, but I'm at work for another hour or so.

---

### Post by abyssspecter on 2006-03-06
[http://img.photobucket.com/albums/v518/AbyssSpecter/Screenshotthing2.png]("http://img.photobucket.com/albums/v518/AbyssSpecter/Screenshotthing2.png")
theres my desktop.

and will that kill all 4 of my panels? or just the main 2?

---

### Post by ComplexNumber on 2006-03-06
go to gconf-editor, type in "panel". there should be a settinng in there that determines the positions of the panels.

---

### Post by Sutekh on 2006-03-06
[QUOTE=ComplexNumber]go to gconf-editor, type in "panel". there should be a settinng in there that determines the positions of the panels.[/QUOTE]

Try this first.

---

### Post by abyssspecter on 2006-03-06
[QUOTE=ComplexNumber]go to gconf-editor, type in "panel". there should be a settinng in there that determines the positions of the panels.[/QUOTE]

where is this? i tried in terminal, and a window popped up. I searched the gconf-editor's and say no 'panel' options.

---

### Post by ComplexNumber on 2006-03-06
[quote=abyssspecter]where is this? i tried in terminal, and a window popped up. I searched the gconf-editor's and say no 'panel' options.[/quote]
there is a tree structure on the left hand side of gconf-editor. click the top of the tree. this means that it will start the search from the top of the tree, and hence, search through all the settings.
now try it.

---

### Post by abyssspecter on 2006-03-07
i still havent found panel positions. ive found panel_size, panel_type, screen, and screen_edge

---

### Post by ComplexNumber on 2006-03-07
[quote=abyssspecter]i still havent found panel positions. ive found panel_size, panel_type, screen, and screen_edge[/quote] type in "panel" i'll have a look myself later and see if i can see anything.

---

### Post by abyssspecter on 2006-03-07
Okay, i did that. I searched through thedifferent branches, and, i saw, under /apps/panel/object/object_# (#=1-17) there were position options, and there were different numbers next to them. what should i do with that?

---

