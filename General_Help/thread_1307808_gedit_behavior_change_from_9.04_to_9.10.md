---
title: "gedit behavior change from 9.04 to 9.10"
date: 2009-10-31
forum: General Help
---

### Post by Razmear on 2009-10-31
In 9.04 when I closed gedit with the cursor at a certain line or section of the file, gedit would go back to that location when it reopened the file so I could start editing right where I left off. 
In 9.10 this feature does not seem to exist anymore and the file opens at the top line of the document. 

Checking to see if it's just me and if this is something that is going to be reworked back to the original behavior, or if there is some setting I forgot I set back in 9.04 that got flipped back. 

eb

---

### Post by mc4man on 2009-10-31
The karmic version (2.28.0) remembers the cursor position but doesn't open the file to it (you can scroll and find 

Maybe file a bug report about it, (i'm sure they'd want to fix or maybe upgrade to 2.29

A quick test using the 2.26.1 source shows it does/can work as expected in karmic

edit:
the 2.29 gedit source also works as expected, now a bit curious, will have to try a local 2.28 build

---

### Post by Razmear on 2009-10-31
I just checked again and this time it opened to the place of my last edit. 
Strange.... 

I did do some tweaking to the fonts and such, but don't know why that would make any difference.... 

Guess I'll see if it happens again and if I can consistently reproduce the issue before going any further. 

About shows my version as gedit 2.28.0

eb

---

### Post by mc4man on 2009-10-31
Is strange- reverted back to 2.28 and still doesn't 'autoscroll' to the cursor (though the cursor is where it was when file was closed.

If you stumble across what changed the behavior do post back.

(I actually find it very handy so will probably use 2.29.1 for the moment

---

