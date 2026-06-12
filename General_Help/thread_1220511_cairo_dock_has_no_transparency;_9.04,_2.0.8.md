---
title: "cairo dock has no transparency; 9.04, 2.0.8"
date: 2009-07-22
forum: General Help
---

### Post by xSauronx on 2009-07-22
seems like every time i get cairo dock to work...it gets broken in an update, and its annoying me to no end. 

i had 1.6.something after an update, before that it worked *Great* and i was happy. should have disabled the repo :-/

anyway, after the update, no compositing. i used windows for a couple months to do some gaming and see what the 7 beta was like, i come back to 9.04 (with gnome and compiz) and do my updates and...cairo dock goes to hell again. no transparency, so its awful. compiz works *fine* so its obviously a cairo-dock thing, but fwiw, im using a radeon 4870 with the 9.6 catalysts. 

i googled a little and searched the forums and didnt find anything relevant. in the past when the transparency broke it was a package problem (no applets, no transparency) and usually just downloading from berlios fixed it *all*. 

i havent done that yet since im using the cairo-dock repo and the applets work. anyone able to point me anywhere before i mess around with it more? i loves my cairo dock when it works.

---

### Post by fabounet on 2009-07-23
cairo-dock -c
until you have real drivers ;-)

---

### Post by xSauronx on 2009-08-01
> **fabounet said:**
> cairo-dock -c
until you have real drivers ;-)

har har

like i said, everyting else works. video still has a few bugs but cairo worked before the update, so its not the drivers :P

any other suggestions?

---

### Post by Favux on 2009-08-01
Hi xSauronx,

Going to 2.x Cairo-dock became OpenGL.  Fabounet is telling you the "fglrx" with Catalyst 9.6 doesn't support OpenGL well enough in Jaunty to get the effects you want.  So instead of the default "cairo-dock -o" (OpenGL) launch with "cairo-dock -c" (Cairo) which is what you had with 1.6 which you said worked.

Or I guess you could check out Catalyst 9.7 and see if ATI's made enough progress.

---

