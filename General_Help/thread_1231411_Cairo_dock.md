---
title: "Cairo dock"
date: 2009-08-04
forum: General Help
---

### Post by Aaron.A on 2009-08-04
hi, 
i can't change my cairo dock icons. i go, rightclick>modify launcher.
and browse to the icon png, ok. and it doesn't work. 

i've tried creating a regular launcher, setting my icon, storing it at home, 
and dragging it to the dock, and i get that damn question mark

i tried google-ing for an answer without much luck. i feel really dumb 
asking. anyone know?

---

### Post by Aaron.A on 2009-08-04
found a solution myself.

it seems to be a problem with wine apps. i'm using a custom launcher, not attempting 
to drag an executable to the dock, but still the icon won't change. even if set before dragging to the dock. 

ok, so since i *can* change all other icons, and i don't need any other wine launchers on my dock, my solution was to change the default-icon.svg found at usr/share/cairo-dock to the icon i want, a photoshop icon. apparently to make an svg you only need to rename a png oO i found that odd. i just wingged it and it worked

hope this helps anyone else running into the problem

---

