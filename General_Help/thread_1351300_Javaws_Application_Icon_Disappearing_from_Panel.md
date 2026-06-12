---
title: "Javaws Application Icon Disappearing from Panel"
date: 2009-12-10
forum: General Help
---

### Post by JasonMU on 2009-12-10
Hi All,

I use the java webstart version of a program called GeoGebra, and after it starts it puts an icon on my desktop which I then move up to the panel.  However, when I reboot the icon disappears.  The application still appears in the cache when I do javaws -viewer.

Any ideas why this might be?  In particular, might this be a problem with the application or with my gnome panel? (BTW, I'm running Karmic, with Sun Java 6)

Thanks for any guidance.
Jason

(BTW, GeoGebra is a fantastic open source mathematics program, similar to Geometer's sketchpad. Among other things, it allows geometrical constructions, graphing, incorporates Yacas and exports graphs to tikz/pgf, pstricks and various image formats. Check it out: geogebra.org).

---

### Post by gordintoronto on 2009-12-10
Do you add it to the panel by right-clicking on the panel and selecting "Add to Panel"?

---

### Post by JasonMU on 2009-12-10
I added it to the panel by dragging the desktop icon it made from the desktop to the panel.  Would that make a difference? I'll give it a try.

---

### Post by JasonMU on 2009-12-10
That seems to have been the problem. I put two icons in the panel, one by dragging the desktop icon to the panel and then deleting the icon on the desktop.  The other I added to the panel by right-click->add to panel.  

Then I logged out and logged back in, and the ex-desktop icon was gone from the panel but the icon I added manually was still there.  

Thanks for the suggestion.  It's strange though because I didn't notice any difference between the two javaws.desktop files in ~/.gnome2/panel2.d/default/  Also, not all of my panel icons are in that directory. Hmm. Well, anyway, thanks again for the suggestion.

---

