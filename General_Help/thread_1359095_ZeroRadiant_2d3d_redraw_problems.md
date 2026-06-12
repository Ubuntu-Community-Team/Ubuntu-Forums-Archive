---
title: "ZeroRadiant 2d/3d redraw problems"
date: 2009-12-19
forum: General Help
---

### Post by rfc on 2009-12-19
I managed to compile ZeroRadiant and run it, however I've graphical problem with the redrawing of all areas. Whenever a window of the application overlaps one of the working areas, it does not immediately refresh the overdrawn area and the space remains occupied until I manually click in the view, in some cases I've to do a small action to force redraw (move camera in 3d view or scroll view in 2d view).

Also showing the entity list dialog and others appear for a second and suddenly get overdrawn with the e.g. 2d view window. The entity list window is still open, but cannot be seen. Only manually moving it around (guessing where it was) will reveal it, but 2d overdraws it most of the time immediately.

I'm running on a Lenovo Z61p with a ATI Mobility FireGL V5200 . I get the feeling it's not a ZeroRadiant specific problem, but maybe a general problem either with Gtk or my graphics driver used or both.

I did not specifically configure my graphics driver (yet) as I wasn't aware of any problems until now. I'm not sure whether the card was detected properly, the Desktop environment just runs fine on 1920x1200 for me.

I also compiled GtkRadiant 1.5.0 (release and branch) and have similar (but not exactly the same) redrawing problems, but I specifically want to focus on ZeroRadiant (i.e. the trunk version).

Any pointers where to start from here?

thx

---

