---
title: "menu_key and run_key for gnome_panel no longer working"
date: 2010-08-09
forum: General Help
---

### Post by geoffjay on 2010-08-09
Ever since installing 10.04 (fresh, no upgrade) I have not been able to Alt+F1 for the gnome-panel menu, or Alt+F2 for the run dialog. The function keys definitely work on their own, eg. F1 opens help. As does other Alt+F# combos, eg. Alt+F4 closes window.

Under gconf-editor at /apps/panel/global/ the values of menu_key and run_key are <Alt>F1 and <Alt>F2 respectively. I've tried changing those to other combinations and the changes don't work either.

This is only happening on one of my computers that run 10.04, and it happens to be the one in my office that I use the most. My PCs at home as well as about a half dozen others here at work were all installed using the same ISO.

As always, any help and suggestions are appreciated. Thanks.

---

### Post by geoffjay on 2010-08-10
Ok, stupid problem fixed. Should have took more time initially to search the Google. Gnome Compatibility wasn't enabled in Compiz.

---

