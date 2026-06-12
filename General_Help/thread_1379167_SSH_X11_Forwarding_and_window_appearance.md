---
title: "SSH X11 Forwarding and window appearance?"
date: 2010-01-12
forum: General Help
---

### Post by CCKrause on 2010-01-12
I recently configured my remote media server system with SSH X11 forwarding  - and it works great: I can run remote applications on my media server with a local GUI on my laptop just fine.

Both systems are running pretty much out-of-the-box installations of Ubuntu Desktop 9.10 with the Gnome desktop.

I'm wondering if I can configure either system so that the appearance settings for windows are different, depending on where the application is running from?

For example: my local machine (the laptop) appearance is configured so that the title bars of applications are a dark blue. I'd like it if the title bar of any window which is attached to an application running on the media server would appear to be a dark maroon color.

Any suggestions about how to do this, or about where I might start looking into this?

---

### Post by sedawk on 2010-01-12
I think everything inside your window is controlled by the
machine where the application is running but the style of
the window frame and icons and menu (resize, max, min,
always on top,etc.) is part of the window manager on the
local machine (where the display is).
What you can do is to change the colors of the stuff
inside the windows. E.g. you can set the background color
of xterms started on different hosts to different colors.
Or you can try to use (slightly) different themes (KDE/Gnome)
on different hosts so that home of different Gnome/KDE app can be
identified by the theme used.

---

