---
title: "Multi-line gnome-panel"
date: 2010-02-04
forum: General Help
---

### Post by Admiral_Payne on 2010-02-04
Does anyone know if it's possible to have a multi-line gnome-panel, without simply increasing the pixel size?

I'd like to be able to have all the small panes in a different place, so the processes aren't crammed together in the middle of the panel #-o

---

### Post by mcduck on 2010-02-04
well, partly.

The Window List-applet becomes multi-line if you make the panel wide enough compared to your application font size. You need twice as much space in the panels as a single button will take (font size plus the badding your GTK theme has set for buttons). But other applets, like the Notification Area, always stay single-lined and instead the size of icons in them increases.

Anyway, as you can have as many panels as you wish, including vertical ones, and the panels are quite customizeable (although some options are only available through gconf-editor), you can get very nice panel setups in Gnome if you want to.. :)

---

### Post by Admiral_Payne on 2010-02-04
Yes, but that would mean that you would need to put a panel on the top, left, right and bottom of your screen if you want to put a lot of crap in it, right?
I just want the panel to sit in the bottom and stop bothering me by being so darn full... without taking anything out ;)

Is it possible to move the current panels I have on/in (how are you supposed to describe that??) the 'overall panel', so that it'd become multi-lined?
It appears like I can only move the panels sideways but not up/down :(

---

### Post by ajgreeny on 2010-02-04
Why not just keep each panel the same size, 24pixels?, but add another panel also on the bottom of the screen.  The result is very similar to a double row and of course you can put your applets on one and the notification area on the other if you want to share out the space used on each.

That's the beauty of linux; you can make it look however you want.

---

### Post by Admiral_Payne on 2010-02-04
> **ajgreeny said:**
> Why not just keep each panel the same size, 24pixels?, but add another panel also on the bottom of the screen.
Ahhhh yes! That's it. Now I've got two panels :)

Do you know if the processes will automatically migrate to the other panel when they're out of space on the first? And now the panels are separated by a line, can I take that away with Appearance prefs somewhere?

---

### Post by ajgreeny on 2010-02-04
> **Admiral_Payne said:**
> Ahhhh yes! That's it. Now I've got two panels :)

Do you know if the processes will automatically migrate to the other panel when they're out of space on the first? And now the panels are separated by a line, can I take that away with Appearance prefs somewhere?
I think not, any more than they would if you left the second panel at the top.  They are quite separate entities.  Just devide all the applets and other items on the two as evenly as you can.  You can try it out and then delete from one and add to the other in a few clicks.

---

### Post by mcduck on 2010-02-05
> **Admiral_Payne said:**
> Ahhhh yes! That's it. Now I've got two panels :)

Do you know if the processes will automatically migrate to the other panel when they're out of space on the first? And now the panels are separated by a line, can I take that away with Appearance prefs somewhere?

No, they won't. Since the panels themselves do absolutely nothing, everything you see in your panels is done by panel applets, which of course is in the panel where you have put it and will not be able to expand to other panels. Also you can't remove the line, the two panels are completely separate from each other (besides, if they would magically combine into one panel you would be back to the one wide panel anyway... :D)

Anyway, your panels don't have to be full-length, and their size & position can be configured quite precisely through gconf. So you could arrange a bunch of smaller panels together to create one larger one with a wide section for the Window List-applet and sections with two panels on top of each other for your other applets, for example.

(by the way, the easiest way to avoid the window list becoming too full is to just start using virtual desktops. I hardly ever have more than a couple of windows per desktop... ;))

---

### Post by Admiral_Payne on 2010-02-05
> **mcduck said:**
> Anyway, your panels don't have to be full-length, and their size & position can be configured quite precisely through gconf. So you could arrange a bunch of smaller panels together to create one larger one with a wide section for the Window List-applet and sections with two panels on top of each other for your other applets, for example.

(by the way, the easiest way to avoid the window list becoming too full is to just start using virtual desktops. I hardly ever have more than a couple of windows per desktop... ;))

Mhm, I'll see if I can tweak it a bit through gconf :)
I'll probably end up using one whole horizontal bar for applications only, and have all the other panels in an other bar.

Yeah I've also been using the virtual desktops, but adding it to panel just made it even smaller and costs an extra click ;) But it'll work.

Thanks for the explanations

---

