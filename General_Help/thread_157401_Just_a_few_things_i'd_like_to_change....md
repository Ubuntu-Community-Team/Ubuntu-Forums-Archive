---
title: "Just a few things i'd like to change..."
date: 2006-04-09
forum: General Help
---

### Post by Pelham123 on 2006-04-09
Hi

3 questions please.

1) How can I get the Terminal window to open in a set position with a custom size?
2) I seem to get 'stacking icons' on my desktop, ie - If I move 2 or more icons to the Desktop they appear on top of each other. No big problem, but I would like to change it.
3) When I use 'Search for files....'  under 'Places' how can I change the default search location from 'Home' to 'Filesystem'?

Thanks!

---

### Post by nanotube on 2006-04-09
[QUOTE=Pelham123]Hi
1) How can I get the Terminal window to open in a set position with a custom size?
[/QUOTE]
i only know how to answer your first question. :)
so, to change size and position of your terminal on start, you have to specify a "--geometry" command line switch. this, from the "man X" page:

> GEOMETRY SPECIFICATIONS
       One  of the advantages of using window systems instead of hardwired terminals is that applications don’t have to be restricted to a particular size
       or location on the screen.  Although the layout of windows on a display is controlled by the window manager that the  user  is  running  (described
       below),  most  X programs accept a command line argument of the form -geometry WIDTHxHEIGHT+XOFF+YOFF (where WIDTH, HEIGHT, XOFF, and YOFF are num&#8208;
       bers) for specifying a preferred size and location for this application’s main window.

       The WIDTH and HEIGHT parts of the geometry specification are usually measured in either pixels or characters, depending on  the  application.   The
       XOFF  and  YOFF  parts are measured in pixels and are used to specify the distance of the window from the left or right and top and bottom edges of
       the screen, respectively.  Both types of offsets are measured from the indicated edge of the screen to the corresponding edge of the window.  The X
       offset may be specified in the following ways:

.................


so, you would want to add ' "--geometry="blabla" ' to the shortcut that you usually use to start your terminal. if you use a kb shortcut to start the terminal, then add it to your terminal in preferred applications panel.

for a few more details, check the link in my sig, and find the "gnome terminal default size" section. ;)

---

### Post by tsb on 2006-04-09
I also would love to stop the stacking icons problem.  Auto align/sort without manually activating it would also be nice.

---

### Post by Pelham123 on 2006-04-09
Thanks Nanotube ;) 

Any takers on the other two?

---

