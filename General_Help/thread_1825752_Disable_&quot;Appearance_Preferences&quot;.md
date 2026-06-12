---
title: "Disable &quot;Appearance Preferences&quot;?"
date: 2011-08-15
forum: General Help
---

### Post by feed5000 on 2011-08-15
I would like to make it so other users on my computer cannot access their Appearance Preferences (right click > change desktop background). I'm searching around and can't find any answers. Anyone know?

---

### Post by flipper T on 2011-08-15
Press Alt+F2 key combination and type gconf-editor in &#8220;Run a command&#8221; box. In next window, navigate to &#8220;apps/nautilus/appearances&#8221; and un-check &#8220;show_dekstop&#8221; in right

this will stop the right click menu appearing, but will also stop any shortcut icons appearing also

---

### Post by feed5000 on 2011-08-15
flipper T's suggestion worked just as I wanted. Thank you! (Only in gconf-editor one needs to locate apps/nautilus/**preferences**.)

---

