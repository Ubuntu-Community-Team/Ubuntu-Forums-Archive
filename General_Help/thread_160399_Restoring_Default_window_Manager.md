---
title: "Restoring Default window Manager"
date: 2006-04-14
forum: General Help
---

### Post by racoq on 2006-04-14
I've unistalled compiz, and i would like x-system of bredzy badger to use its default window manager, can anyone please tell me how to do it? (My windows are without frame and buttons, so please help me)

---

### Post by Ramses de Norre on 2006-04-14
echo export WINDOW_MANAGER=/usr/bin/metacity >> ~/.gnomerc
If it doesn't work try rm ~/.gnomerc

After doing one of the above, run metacity (type it in terminal), save session and log back in.

---

