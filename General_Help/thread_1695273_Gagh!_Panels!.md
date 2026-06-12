---
title: "Gagh! Panels!"
date: 2011-02-25
forum: General Help
---

### Post by Mainewha on 2011-02-25
I was messing around a little with the panel at  the top of the screen when I removed something I really didn't want to remove. How can I restore the main menubar thing to have all of the original buttons and the like without having to reinstall and start over?

---

### Post by howefield on 2011-02-25
It might be easier to restore the panels to default, and then put back your customisations, if you had any.

Terminal commands as follows.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

---

### Post by Mainewha on 2011-02-25
the first part was what I needed. Thank-you!

---

