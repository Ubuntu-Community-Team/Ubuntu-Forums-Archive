---
title: "Maximus is misplacing windows"
date: 2010-11-20
forum: General Help
---

### Post by mb_webguy on 2010-11-20
After giving it a try for the last month, I decided to ditch Unity and switch to the EFL version of the old netbook launcher.  To gain the ability to modify the panel, I followed the steps on [this page]("https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession") to convert the normal Gnome session to emulate the netbook remix session.

It worked... sort of.  My problem is that certain applications are being misplaced by Maximus.  I first noticed the problem after I set the top panel to auto-hide, at which point certain apps, like gnome-terminal, weren't being maximized.  After I disabled auto-hide on the top panel, gnome-terminal and certain other applications are being maximized, but they're shifted down so that there's a sizable gap between the top of the window and the panel.  To make things even more interesting, window controls are still where they're supposed to be as far as clicking with the mouse is concerned, so that I have to click where a certain object should be rather than where it *is*.  

I've tried deleting the Gnome configuration directories (e.g. .gnome, .gnome2, .gconf, etc.), but other than resetting my panels, it didn't have any effect.

Any ideas?

EDIT:  If I unmaximize a window and then maximize it manually, it displays correctly, so it seems like the problem has to be with Maximus...

---

### Post by kerry_s on 2010-11-20
my guess would be some unity settings left behind.

check in gconf-editor see whats in the exclude_class

i'm using the normal gnome desktop with awn & maximus

---

