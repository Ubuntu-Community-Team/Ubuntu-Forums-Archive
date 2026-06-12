---
title: "lost my gnome panel"
date: 2010-09-10
forum: General Help
---

### Post by duncan503 on 2010-09-10
hello for some reason I delete my lower and top gnome panel and would like to find out if their is a way of recovering it or replacing it.
Thank you for the help;

---

### Post by msrinath80 on 2010-09-10
> **duncan503 said:**
> hello for some reason I delete my lower and top gnome panel and would like to find out if their is a way of recovering it or replacing it.
Thank you for the help;

Chances are you only made it transparent and thus, invisible. You can delete all but one panel. Gnome is very stubborn about this. Try typing "ps aux | grep panel" in a terminal window and see if gnome-panel is running. I'll bet you anything it is*.

* Unless of course you either renamed the gnome-panel executable to something else or went into the gconf-editor and under required components for gnome, you removed the panel entry thus not requiring the panel to start along with gnome.

Either way, my apologies. The suggestions above aren't necessarily helpful in getting you to solve your problem. Try searching around in this forum for a lost panel. You should find some helpful threads.

Usually, killing X and restarting helps. Extreme measures involve getting rid of .gnome or .gnome2 directories and starting from scratch. But either way please wait for someone else to respond.

---

