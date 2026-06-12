---
title: "Ways to declutter font menu? Including removing foreign fonts"
date: 2012-05-23
forum: General Help
---

### Post by the big e on 2012-05-23
As others might have also experienced, the font menu has so many things in it, it is hard to see what they all are. I find this very annoying. 

This includes, notably, foreign-language fonts for languages I don't write in.

Is there anything like, for instance, a one-line command for removing all foreign language fonts?

Is font-menu customizing something I need to do separately for separate applications?

(I think I want to keep all the symbol fonts and math fonts and stuff, but remove all the alphabets I don't read.)

Is there a way to turn fonts off in the menu without uninstalling them? A way to look at certain small groups of fonts in the menu and switch between them?

---

### Post by Enigmapond on 2012-05-23
No one line command that I know of. Install font-manager and see if that helps.

---

### Post by wrknight on 2013-02-20
If you find unwanted fonts that can't be removed by Font Manager, it's probably because they are write protected and hidden in directories in /usr/share/fonts.  You can remove them by brute force, buy you must have superuser priveleges.  Locate the offending fonts and use the *sudo rm* command to remove the font files.  Then you can remove the unwanted directories by using the *sudo rmdir* command. :)

---

