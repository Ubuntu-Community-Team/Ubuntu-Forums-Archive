---
title: "Gnome panel visible over Impress/Presenter slide"
date: 2010-01-18
forum: General Help
---

### Post by n.l.o on 2010-01-18
When I run a slide show (F5), the Gnome panel is shown in the screen.
Sometimes it is hidden below the slide show, but usually the panel is shown.

How do I make it hidden during a slide show or is this some kind of bug? 
Did not find anything on google.

Open Office 3.1.1 (Build:9420)
Gnome panel 2.26.0

Magnus

---

### Post by flipper9 on 2010-03-16
I've got the same problem with Impress (Open Office bundled with Lucid).  The gnome panel is still visible when running Impress presentations full-screen (using F5) with the entire slide shifted down, and the bottom bits of the slide cut-off.

---

### Post by jatinps on 2010-04-14
did anyone figure out a way of resolving this?

---

### Post by n.l.o on 2010-04-14
It is Compiz/OO that interfers, there is something about a full screen request from OO that is not recognised by Compiz WM (dont know the details, but there is a bug filed). 

"solution 1": disable the "place" plugin in Compiz, you have to go in to preferences and turn off automatic plugin sorting, and then disable it.

"solution 2": turn autohide on, for the panel that it is not covering (I did that, easy to do just be4 you present).

"solution 3": turn compiz off completely and use e.g. metacity that does not mess it up.

"solution 4": save your pres as a pdf and use evince.

"solution 5": I think you can compile OO from scratch having changed this fullscreen request to something compiz likes (the insane solution).

cheers.
Magnus

---

