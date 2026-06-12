---
title: "remove empty panel from desktop"
date: 2009-11-12
forum: General Help
---

### Post by tom.swartz07 on 2009-11-12
Hi all,

I have a bit of an annoyance.
I was showing my friend how to add a panel to their desktop by using my system, and I added an empty panel to the left hand side of the desktop. After I showed him the process of adding it and adding/removing launchers, I accidentally exited out of the panel properties window, leaving an empty panel stuck on my screen. Since it was set to auto-hide, it shrank down, and now will not come back out, leaving me clueless as to a method of removing it.

Normally, this wouldnt be an annoyance, but I have my panels set to show a row of 2px even when minimized, and I would not like to change that for the sake of a dumb empty panel.


Does anyone know of a method to get rid of this troublesome stuck panel, aside from removing the entire panel application and re-installing?

Thanks,

---

### Post by mechro on 2009-11-12
In **Applications > System Tools > Configuration Editor** navigate to **apps/panel/toplevels**. In there you'll find entries for your panels. Find the one that has an **auto_hide **setting checked and uncheck it.

If you haven't got the Gnome Configuration Editor installed you can get it via Synaptic.

---

### Post by tom.swartz07 on 2009-11-12
> **mechro said:**
> In **Applications > System Tools > Configuration Editor** navigate to **apps/panel/toplevels**. In there you'll find entries for your panels. Find the one that has an **auto_hide **setting checked and uncheck it.

If you haven't got the Gnome Configuration Editor installed you can get it via Synaptic.

NICE! I looked there before, but I wasnt sure about what exactly to try, and I didnt want to break something with my incessant tinkering.

It was Panel_0, and after I unchecked auto-hide, I was able to delete it.

/thread solved.

---

