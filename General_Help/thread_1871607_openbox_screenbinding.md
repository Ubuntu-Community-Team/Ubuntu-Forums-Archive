---
title: "openbox screenbinding"
date: 2011-10-29
forum: General Help
---

### Post by dzon65 on 2011-10-29
Hi. I added this part to my openbox rc.file, <keybind key="A-C-q">
   <action name="ShowMenu">
     <menu>root-menu</menu>
   </action>
 </keybind>, which will popup the openbox menu wherever the mousepointer is.
I'd like to add a screenbinding though, say hovering the left of the screen, making it pop up in the center of the screen using xautolock. So, I added this part to my autostart file:
xautolock -locker  "xte'Ctrl+Alt+q'" -corners 0+00  -cornerdelay 1 &, which should make it pop up when the top right corner is hovered, which it doesn't of course, since it's set to open wherever the mousepointer is.

So, two questions. How do I set it to open centered on the screen and what's the left side setting for xautolock?

---

