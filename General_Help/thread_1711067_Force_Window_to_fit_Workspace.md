---
title: "Force Window to fit Workspace"
date: 2011-03-20
forum: General Help
---

### Post by neu5eeCh on 2011-03-20
OK, I've given up on tiling workspaces vertically. How about forcing a window to fit in a workspace? Any suggestions?

---

### Post by Krytarik on 2011-03-20
This depends on which window manager you are running.

If it is Compiz, you can use its "Window Rules" plugin to achieve that:
"System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Window Rules -> Size (tab)"

There you can set up different rules, if you just want *all* windows to fill the workspace, set the window match (field "Size Windows") to "any" and "Width"/"Height" according to your screen resolution. If you want to be exact there, grab the "Height" of a maximized window with the command "xwininfo". To exclude dialog boxes from those rule, set the window match to "!type=dialog".
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

If you want to achieve that with Metacity, you have to use "Devilspie", its in the official repos.
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

