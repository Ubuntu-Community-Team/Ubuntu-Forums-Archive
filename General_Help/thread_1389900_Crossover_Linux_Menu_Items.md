---
title: "Crossover Linux Menu Items"
date: 2010-01-25
forum: General Help
---

### Post by yousillygoose on 2010-01-25
Hey hey,

I've been using crossover linux for quite some time now.  For all previous Ubuntu editions that I have run (since Gutsy), Crossover makes it's own menu in the Gnome Application Menu that links the user to the installed Windows software.  I can't seem to get crossover to automatically install the menus in 9.1.  Is anyone else having this problem?  Is there any solution out there?

Thanks!

ysG

---

### Post by yousillygoose on 2010-01-25
I actually solved the problem solo.  Alacarte requires sudo in 9.1.  To edit the menu, administrative access was needed and I assume crossover did not fit the category.  A simply chowned two directories and ran:

/opt/cxoffice/bin/cxmenu --crossover --install

and bingo- menus fixed :)

---

### Post by raonyguimaraes on 2010-02-19
This command works like a charm on my karmic with Crossover 8 !!!!!

---

