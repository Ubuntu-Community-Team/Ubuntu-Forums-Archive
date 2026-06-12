---
title: "ubuntu 10.04 start script"
date: 2010-07-27
forum: General Help
---

### Post by nixIT on 2010-07-27
Greetings all,

today I installed the Ubuntu 10.04 start script(found [here]("http://helpdeskgeek.com/windows-xp-tips/easily-customize-a-fresh-install-of-ubuntu-10-04-with-a-script/") to help install many of the extra items that one would need.

however, after I installed the script and selected only the options I wanted, things have been weird.

For instance, when I open up nautilus, there is a plus sign (+) next to the folder names, not a triangle like before.  The plus sign is "ok", but it looks out of place.  Any way to get the triangle back?  I tried changing themes and that did not help.

Is there a way to uninstall the "tweaks" that the Ubuntu 10.04 start script adds, changes?

--nixIT

---

### Post by rubylaser on 2010-07-27
Just re-run the script, it looks like it contains a reset for each of the options that you you changed.

---

### Post by nixIT on 2010-07-27
> **rubylaser said:**
> Just re-run the script, it looks like it contains a reset for each of the options that you you changed.

thanx, I reset the options I changed, but the + is still next to the folder names.  

I just launched gconf-editor, and in the left hand pane, there are plus signs there too, so it's a system setting someplace.

hrrmmmmmm.

--nixIT

---

### Post by nixIT on 2010-07-28
Changed the "Controls" in themes to industrial and the triangles are back.  So it appears it wasn't the start script though a controls option.

--nixIT

---

