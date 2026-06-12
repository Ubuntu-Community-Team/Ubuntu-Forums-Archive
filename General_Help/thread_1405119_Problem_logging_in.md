---
title: "Problem logging in"
date: 2010-02-12
forum: General Help
---

### Post by bjarkith on 2010-02-12
Im running Ubuntu 9.10 and I added a new panel to my desktop and had it on autohide and not expanded, when I did this my computer froze, and now everytime I try to log in it freezes at the ubuntu loging screen after I type in my password. Anyone had this problem or know how to fix it?

With regards, Bjarki

---

### Post by ironclaw on 2010-02-13
It seems like the new panel is somehow making the gnome desktop freeze, so you should probably remove it. To do this, log in on a virtual terminal by pressing <Ctrl>+<Alt>+<F1> and type in your username and password.

The panel configuration should be in ~/.gconf/apps/panel/toplevels/. In my configuration, there are three files there: bottom_panel_screen0  %gconf.xml  top_panel_screen0. I think you can remove a panel just by deleting the corresponding file or moving it somewhere else.

So run
```
mv ~/.gconf/apps/panel/toplevels/<name of panel> ~/.panel.bak
```
to remove the panel.

---

