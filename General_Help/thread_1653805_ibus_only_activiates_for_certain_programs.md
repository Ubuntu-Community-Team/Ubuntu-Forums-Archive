---
title: "ibus only activiates for certain programs"
date: 2010-12-27
forum: General Help
---

### Post by Hsiu on 2010-12-27
SOLVED: While ibus and ibus-qt4 had been installed, ibus-gtk had not, hence it not working in GTK applications.

Hello,

After trying scim and being unable to get it to work at all (it shows up in the task bar, but no key combination I set activates it, also skim wouldn't execute because ti couldn't find drkonqi), I tried ibus. I've got it working and able to activate, but only in certain applications - open office and kate for starters, even xterm.

Apps that are more important to me as far as being able to enter traditional Chinese - namely Firefox and gvim - I can not activate the IME for - I hit the key combo I set up which works in OOo and kate, but to no avail. Firefox and gvim both use GTK, so I thought maybe that had something to do with it. Scim/skim required me to set QT_IM_METHOD and GTK_IM_METHOD - I have tried doing this with ibus, as well, but they always seem to get clobbered, so that didn't help either way.

Any advice?

---

