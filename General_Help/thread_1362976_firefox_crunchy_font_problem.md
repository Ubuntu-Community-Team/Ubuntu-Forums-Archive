---
title: "firefox crunchy font problem"
date: 2009-12-23
forum: General Help
---

### Post by sototallycarl on 2009-12-23
See attached screenshot. On the left, Firefox 3.5.6 the right Chromium Nightly. Firefox looks like there is no (or bad) aliasing and Chromium has it right. I have the font settings set correctly where everything looks nice in gnome including all Firefox menus but when the page renders all type looks terrible.

Any way to fix this?

---

### Post by dcstar on 2009-12-23
> **sototallycarl said:**
> See attached screenshot. On the left, Firefox 3.5.6 the right Chromium Nightly. Firefox looks like there is no (or bad) aliasing and Chromium has it right. I have the font settings set correctly where everything looks nice in gnome including all Firefox menus but when the page renders all type looks terrible.

Any way to fix this?

Firefox render fonts differently from FF 3.0 and other apps - it apparently does not use the Gnome settings any longer.

You can search out posts on how to modify other font settings to fix the rendering.

---

### Post by cottfcfan on 2009-12-24
Many of us have the same problem with Firefox, that`s why i now use chromium.
There is a firefox-smooth-fonting ppa that you can add to your repos, which helps, but it seems its not yet working with Firefox 3.5.6

---

### Post by wojox on 2009-12-24
Edit -> Preferences menu item (pick General, and click on "Fonts & Colors"). Pick a larger font, reload the page, and see how it looks. Of ocurse, you can also just use the key combination Ctrl-+

---

### Post by cottfcfan on 2009-12-24
Wojox,

Changing the font or using CTL+ makes no difference, if your screen uses a high resolution ie 1650 x 1050, the bigger you make it the more pixelated it becomes, ive only found the above ppa that helps, but it dosent seem to work yet in anything higher than 3.5.5.

---

