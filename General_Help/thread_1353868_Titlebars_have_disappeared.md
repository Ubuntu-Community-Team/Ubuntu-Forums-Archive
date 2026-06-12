---
title: "Titlebars have disappeared"
date: 2009-12-13
forum: General Help
---

### Post by geeare1 on 2009-12-13
Hi,

I've been using Ubuntu 9.04 for a few months with great results. However, for some reason, I no longer have titlebars on any of the windows.

While there are keyboard shorcuts to get around this problem I'm wondering if this has happened to anyone else and, if so, how can I fix it?

Thanks very much,
gary

---

### Post by Anzan on 2009-12-13
It's a Compiz thing.

Go to System/Preferences/Appearance.

If you turn off the effects, Metacity will be your WM.

If you still want effects, try choosing items from the Advanced menu and they should come back. 

You might need to log out and back in.

I forget. I'd had this happen a few times wih Compiz a few years ago so gave up on it.

---

### Post by geirha on 2009-12-13
Sounds like a problem with gtk-window-decorator. Do they come back if you hit Alt+F2 to get the run-dialog, and run «gtk-window-decorator»?

See if there's any errors regarding gtk-window-decorator in .xsession-errors.
```
gedit ~/.xsession-errors
```

---

