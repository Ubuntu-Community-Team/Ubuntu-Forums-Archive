---
title: "Theme help - where did they go?"
date: 2009-11-18
forum: General Help
---

### Post by ed-koala on 2009-11-18
I just downloaded and installed a few new themes for my desktop.  Clicked install, things went fine, but they don't appear under the themes tab. What gives?  There's no option to uninstall and it wont reinstall - can't move directory over directory.

Where are they?

---

### Post by VCoolio on 2009-11-18
They are in ~/.themes if they were gtk or metacity themes, or in ~/.icons if they were icon themes. If it's a gtk theme without metacity or the other way round it's not a 'complete' theme and it won't show up directly in the appearance window, but click 'customize' and your gtk2-themes should be under 'controls' and metacity-themes under 'borders'.

---

### Post by MonoDeem on 2009-11-18
Some of them doesn't appear because they are incomplete. Click on any theme and select Customize - browse through the given tabs and you'll ( in most cases ) see it there.

---

### Post by ed-koala on 2009-11-18
Thank you, that helped me understand things a bit better.

---

### Post by emigrant on 2009-11-18
themes only for you go here:
~/.themes

and shared themes go here:
/usr/share/themes

---

