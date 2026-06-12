---
title: "Delay for panel to unhide"
date: 2010-01-10
forum: General Help
---

### Post by patman0623 on 2010-01-10
I particularly enjoy the feature in which I can make the top (or bottom) panel hide itself until I hover the mouse near. However, the delay until it appears is excruciatingly long (500ms might not sound like a lot, but when you do it dozens of times per hour, it can be a bit irking)

Is there a way to decrease this time?

---

### Post by Geoff918 on 2010-01-12
You're looking for gconf-editor (which is for GNOME).

Do an Alt-F2 input gconf-editor

Select:

Apps -> Panel -> TopLevels -> Bottom_Panel_Screen0 -> hide delay / unhide delay

You're actually right it seems to default to 500ms. Good job keeping count on your fingers while saying 'milli-mississippi' five-hundred times.

I hope this helps, Pat. If you have any other questions, just call me when you're able to talk again--hope the surgery went well!

---

