---
title: "Transparent window"
date: 2010-02-05
forum: General Help
---

### Post by frbaresi on 2010-02-05
Hy all,
Is there any way to draw semi-transparent windows, using GTK or Xlib, without using a composite manager? (I can't use xcompmanager, compiz or any other composite manager)

The best I could do until now, was to put an image in a window and make all transparent around the image. Something like this:

[http://www.gtk.org/tutorial1.2/gtk_tut-9.html#ss9.6]("http://www.gtk.org/tutorial1.2/gtk_tut-9.html#ss9.6")

Thankx

---

### Post by MichealH on 2010-02-05
Have you tried metacity compositing?

---

### Post by frbaresi on 2010-02-05
No, but I do not want to use a composite manager because, everytime I use them, the performance of my system is worse.... I notice the difference because I use this system as a video player

Another thing that keeps away me from the composite managers,is the fact that I do not want to degrade the performance of my system because of a single window.


Thankx

---

### Post by MichealH on 2010-02-05
I have used Metacity Compositing and have never looked back I find no performance flaws when using the compositing manager. And I have a SiS card (which is unsupported)

---

### Post by lidex on 2010-02-05
> Is there any way to draw semi-transparent windows, using GTK or Xlib, without using a composite manager?
I don't think so. Metacity has a fairly low overhead, do you have a low-powered system? Also compiz can be switched on and off easily with the fusion-icon:
> This package contains a tray icon that allows you to easily enable, disable and
restart Compiz, and change the currently used window manager and/or window
decorator.

---

### Post by frbaresi on 2010-02-08
Finally I am using metacity as a composite manager...but Yet I have a problem.
When I draw a window with opacity < 1 (gtk_window_set_opacity(GTK_WINDOW(window),0.4) ), the window is drawn as if it were fully transparently.

Any idea?

---

### Post by frbaresi on 2010-02-08
Just one update.
I found this:
"Compositing permits advanced visual effects by using buffers and manipulating the images before they appear on the screen. In *Metacity*, these effects include window shadowing, smoother window movement, and thumbnail views when using *ALT-Tab* to switch between windows."

[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

Thankx

---

