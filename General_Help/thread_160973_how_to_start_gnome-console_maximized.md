---
title: "how to start gnome-console maximized?"
date: 2006-04-16
forum: General Help
---

### Post by lezz on 2006-04-16
1. what is the console command to start gnome-terminal maximized?

2. is it possible to choose on which desktop (i've got 4) gnome-terminal will be started?

---

### Post by nanotube on 2006-04-16
don't know how to choose the desktop, but you can choose size and position of the window with the "--geometry" command line option. see "man gnome-terminal" and "man X" for more details on the geometry specification.

---

### Post by elamericano on 2006-04-16
That's the right way. To add that to the menu launcher:

Applications->System Tools->Applications Menu Editor
Select Accessories
Right Click on Terminal
Add  --geometry=125x37+0+0 to the end of the command

where geometry=<width>x<height>+<x-pixels>+<y-pixels>

If you wanted to make it truly global, you could try to edit /usr/share/vte/termcap/xterm - but I don't recommend that.

---

### Post by elamericano on 2006-04-16
Your second question got me thinking, because it would be nice to open up a lot logs and diagnostics in another workspace to be ready when I need them, but from what I gather, metacity, gnome's default window manager, does not include this functionality. (I'm becoming more and more disenchanted with gnome. Maybe I'll switch to the kubuntu side)

Anyway. You can switch your window manager to something that supports it (sawfish, fvwm, blackbox, etc.), and launch a shell script from your icon, OR you can try this little add-on:
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

---

