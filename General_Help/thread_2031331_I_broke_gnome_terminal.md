---
title: "I broke gnome terminal"
date: 2012-07-21
forum: General Help
---

### Post by sky5564 on 2012-07-21
I was playing around with the setting in gnome terminal and i selected "run this command instead of termial" and now when i start the terminal it immediatly closes.:confused:

---

### Post by Quackers on 2012-07-21
If you go into gconf-editor you can browse to 
/apps/gnome-terminal/profile/default/custom_command
and make the necessary change there.

---

### Post by Giant Speck on 2012-07-21
1.  Open the Configuration Editor (gconf-editor)
2.  Expand the **apps** folder
3.  Within the apps folder, expand the **gnome-terminal** folder
4.  Within the gnome-terminal folder, expand the **profile** folder
5.  Select the **Default** folder
6.  Find and uncheck the **use_custom_command** option
7.  Close the Configuration Editor

If it doesn't work right away, try restarting your computer.

---

### Post by sky5564 on 2012-07-21
Thanks that fixed it, Although i must mention that gconf editor is not installed in ubuntu 12.04 but after i installed it was an easy fix, Thanks guys.:P

---

