---
title: "help making gnome preload ALL icons into memory."
date: 2006-06-23
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-23
hey all, Gnome seems slightly slow to me as far as icon loading and such, I would assume such things would travel much faster if the icons and everything were loaded into memory right before the desktop even displayed... is there any way to do such things without using pre-link or preload? I would assume that you can change such setting... and, I would also assume that ALL the icons would probably only use up 3-5MB of ram. so it really wouldn't be an issue to me.... anyone have any idea whatsoever as to how this could possibly be done?


I get a quarter second delay when I open top menus, this generally only happens once because the icons get loaded into memory after first load.

anyways...if anyone has any idea please please PLEASE tell me.


thank you

---

### Post by Patrick-Ruff on 2006-06-23
need I make my question any clearer???

---

### Post by maxpower on 2006-09-26
Not sure how much it will help, but I have used the following command with varying results:

```

gtk-update-icon-cache /path/to/icon/theme

```

mAx

---

