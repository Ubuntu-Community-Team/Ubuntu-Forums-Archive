---
title: "maximalized windows over tint2"
date: 2010-03-07
forum: General Help
---

### Post by literos on 2010-03-07
hi im using ubuntu for a long time now and i intalled tint2 recently but if i maximalize window there is gap between end of that maximalized window and end of my screen and that gap is where my tint2 is...so my question is, can i configure tint2 that if i maximalize window it will be over whole screen?

---

### Post by thil77 on 2010-03-08
with tint2-0.9 you have autohide capability.
see [http://code.google.com/p/tint2/wiki/Configure#Panel_autohide](http://code.google.com/p/tint2/wiki/Configure#Panel_autohide)


and in SVN version, you have another way to do this :
> 
panel_layer = bottom
strut_policy = none


see the end of panel option 
[http://code.google.com/p/tint2/wiki/Configure#Panel](http://code.google.com/p/tint2/wiki/Configure#Panel)

---

### Post by literos on 2010-03-08
thanks lot it worked. I just had an old version of tint :)

---

