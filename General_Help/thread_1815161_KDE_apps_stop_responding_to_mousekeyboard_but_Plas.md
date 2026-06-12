---
title: "KDE apps stop responding to mouse/keyboard but Plasma still works"
date: 2011-07-30
forum: General Help
---

### Post by mfeltman on 2011-07-30
Hey folks.  I'm not sure how to describe this properly but periodically Kubuntu 11.04 will stop responding to my mouse and keyboard EXCEPT that Plasma, or what I assume is Plasma, still responds to mouse events.  I can launch and exit the desktop cube and desktop grid but can't access my panels or any application controls.  The only fix I've found is to do a hard power cycle.

Does this behavior ring any bells for anyone?  This is the last hurdle I've got between me and using Kubuntu 11.04 full time on my Samsung RV515.

---

### Post by mfeltman on 2011-07-31
Bump.  

Still can't figure this one out, guys.  Any guidance?

---

### Post by samigina on 2011-08-01
Press crtl+alt+f1

Login in the new console session and type "top", just to see if theres any procces hanged. If cant shutdown from the graphic session you can shutdown from the console typing "sudo shutdown now"

With Crtl+alt+f7 you can back to the original, graphic session.

And try to see you System log, if asomething is wrong it should be there.

---

