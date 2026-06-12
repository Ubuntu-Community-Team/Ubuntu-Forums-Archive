---
title: "ttf-mscorefonts-installer behaves oddly"
date: 2011-09-19
forum: General Help
---

### Post by Leprkan on 2011-09-19
Normally this package is said to be the remedy for wonky fonts.  Oddly this has exactly the *opposite* effect for me. 

Thoughts? Solutions? Metaphysical ponderings?

Edit: It only affects Chromium.

---

### Post by Krytarik on 2011-09-19
Just run the below command, and handle the upcoming confirmation dialog with Tab, Arrow keys and Enter. You may have missed this or another form of dialog in the first place.
```
sudo dpkg --configure -a
```
Greetings.

---

