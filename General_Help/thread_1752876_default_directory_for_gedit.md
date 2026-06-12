---
title: "default directory for gedit"
date: 2011-05-08
forum: General Help
---

### Post by UR Data on 2011-05-08
Hello!

I configured the shortcut Alt+G to fire up mini editor gedit, which is fine. But when I press Ctrl+O to open a file, it searches directory /, the very root. While I want it to open automatically in /home/urdata/java/, for instance.

The man-page doesn't tell me and the Preferences... inside gedit do not cover it, it seems. Can you tell me how?

-UR Data

---

### Post by hwttdz on 2011-05-09
Looks like it defaults to the current directory.  So try changing your launcher to either 
cd ~; gedit
or 
export PWD="~" && gedit
or some mix and match of semicolons and &&'s.  I'm not sure which is considered more appropriate if both work.

---

