---
title: "Eclipse 3.5 Not repainting the screen"
date: 2009-12-08
forum: General Help
---

### Post by jokerr on 2009-12-08
I'm using the Ubuntu approved version of Eclipse 3.5 (experienced the same issue w/ a manual install) and I've noticed that my Eclipse window does not repaint properly, mainly in the "install new software" modal windows.

Allow me to elaborate:
[LIST]
[*]Open Eclipse 3.5 > Help > Install New Software
[*]Select Eclipse Web Tools for example
[*]The screen will never repaint and no items will be available in the selection boxes.
[/LIST]

I've left this screen alone for 5+ minutes thinking maybe I had a bad connection but it still does not repaint.  Only by expanding/collapsing the modal window does it force a repaint however this does not work all the time.  When it does work the Next button doesn't repaint the screen to show me the next options...  This basically means I can't install any plugins for Eclipse :(

I'm running Ubuntu 9.10 32bit version and using sun-java6.  I've tried with Visual Effects turned off and in Normal mode (System > Preferences > Appearance > Visual Effects).  My graphics card is a Nvidia 6600GT w/ direct rendering turned on.  I'm stumped on this one, any help is appreciated.

---

### Post by PeEllAvaj on 2009-12-08
Are you using Kubuntu?  I had a very similar problem:
[http://mortalpowers.com/news/quick-fix-buttons-stay-depressed-in-eclipse-and-other-gtk-applications-under-karmic-with-kde](http://mortalpowers.com/news/quick-fix-buttons-stay-depressed-in-eclipse-and-other-gtk-applications-under-karmic-with-kde)

Is this your issue?

---

### Post by jokerr on 2009-12-08
> Are you using Kubuntu? I had a very similar problem:
[http://mortalpowers.com/news/quick-f...armic-with-kde](http://mortalpowers.com/news/quick-f...armic-with-kde)

Is this your issue?

No, I'm using Ubuntu however this fixed worked!  Thank you very much.

---

