---
title: "Fonts in firefox awful"
date: 2009-07-29
forum: General Help
---

### Post by vinutux on 2009-07-29
After install **ttf-mscorefonts-installer** my firefox look awful (menus, ubuntuforums etc).....i want my [COLOR="DarkOliveGreen"]**good-looking**[/COLOR] firefox back without uninstall ttf-mscorefonts-installer.....Any ideas ?
**[SIZE="7"][COLOR="DarkGreen"]SOLVED[/COLOR][/SIZE]**:D


Deleting .font.conf fixed

---

### Post by CatKiller on 2009-07-30
Edit &#8594; Preferences &#8594; Content &#8594; Fonts & Colors &#8594; Advanced...

Pick some fonts that you like and untick the "Allow pages to choose their own fonts" box.

The menus are chosen by the Application font setting of System &#8594; Preferences &#8594; Fonts.

---

### Post by vinutux on 2009-07-30
> **CatKiller said:**
> Edit &#8594; Preferences &#8594; Content &#8594; Fonts & Colors &#8594; Advanced...

Pick some fonts that you like and untick the "Allow pages to choose their own fonts" box.

The menus are chosen by the Application font setting of System &#8594; Preferences &#8594; Fonts.

Thnks..but i am still missing something...Menues not lookig good as earlier

which is fonts ubuntu using in font settings default

---

### Post by vinutux on 2009-07-30
WOW..............fixed

Deleting both .fontconfig folder and [COLOR="Red"].fonts.conf[/COLOR] fixed problem.....

because after installing microsoft ttf fonts it create a configuration file in my home folder "fonts.conf"......deleting it fixed......now everything running smooth.....

---

