---
title: "Invisible panel?"
date: 2010-08-17
forum: General Help
---

### Post by forsaken_pariah on 2010-08-17
So I just did a clean install of Ubuntu Lucid on a friend's computer, and I seem to have a very interesting problem...

On the very first startup, there was no gnome-panel running at all. Running gnome-panel from the terminal started the panel with no problem, so I tried adding gnome-panel to the startup applications. Now I get an empty space on the top of there screen where the panel is supposed to go, but alas, there is no panel there, and running gnome-panel from the terminal  returns an error that there is already a panel running. Running gnome-panel --replace from the terminal, however, starts the panel with no problem again.

This happened on the first boot, and still continues to do so after installing all updates. A failsafe session gives me absolutely no trouble at all. It almost seems like there's something going on in my startup script that's foobaring my panel, but I can't find anything, and I have made absolutely no changes to the system since install other that what I listed here. What could possibly cause this to happen??? I'm totally lost. Any help is greatly appreciated.

---

### Post by forsaken_pariah on 2010-08-20
Nobody?

---

### Post by Frogs Hair on 2010-08-20
Try right clicking where the panel should be and select new panel , then right click the panel  and select  add to panel in order to add the desired items.

---

### Post by onivan on 2010-10-22
What helped for me:
Press <Control>+<Alt>+Tab and choose the invisible panel. Then you can right-click it and do all you need to it.

---

