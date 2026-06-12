---
title: "Gtk Programming"
date: 2010-07-15
forum: General Help
---

### Post by supravat on 2010-07-15
I have created a window using gtk+ programming. But when I'm running the program the window is appearing any where of the screen. Is the any way or function so that window will always appear at the center of the screen ???

Please help me...

---

### Post by mac9416 on 2010-07-15
Hi, supravat,

What language are you programming in?

If C, here's the documentation for setting a window's potition: [http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-position](http://library.gnome.org/devel/gtk/unstable/GtkWindow.html#gtk-window-set-position)
Here are the constants you can pass to that function: [http://library.gnome.org/devel/gtk/unstable/gtk3-Standard-Enumerations.html#GtkWindowPosition](http://library.gnome.org/devel/gtk/unstable/gtk3-Standard-Enumerations.html#GtkWindowPosition)

If Python:
Here's the set_position function: [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-position](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-position)
And here are the constants: [http://www.pygtk.org/docs/pygtk/gtk-constants.html#gtk-window-position-constants](http://www.pygtk.org/docs/pygtk/gtk-constants.html#gtk-window-position-constants)

I hope that helps!

---

