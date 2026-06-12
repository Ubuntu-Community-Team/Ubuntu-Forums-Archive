---
title: "Help, I have no window manager!"
date: 2006-06-06
forum: General Help
---

### Post by web250 on 2006-06-06
I got this bad bug #46189...so I had to reinstall, but I kept my /home folder alone.

When I boot back up with my fresh /, it loads into X, but I have no window manager. All the windows have no borders, the taskbar at the bottom doesnt show which apps are open, etc...

Whats the fix?

---

### Post by givré on 2006-06-06
What's happens if you run ```
metacity
``` in a terminal?

---

### Post by matrooswolf on 2006-06-06
```
metacity --replace
```
what does that do?

---

### Post by .t. on 2006-06-06
I think that that sets metacity as your default window manager. compiz uses the --replace command to tell gconf that it's the window manager.

---

### Post by givré on 2006-06-06
[QUOTE=.t.]I think that that sets metacity as your default window manager. compiz uses the --replace command to tell gconf that it's the window manager.[/QUOTE]
In fact, we use --replace because you couldn't have two window manager running, so it is just to replace the current WM by the new one.

---

### Post by web250 on 2006-06-06
Metacity wasnt installed for some odd reason. Installed it and it fixed everything. Thanks!

---

### Post by mlind on 2006-06-06
[QUOTE=web250]Metacity wasnt installed for some odd reason. Installed it and it fixed everything. Thanks![/QUOTE]

Metacity was missing? You better also check that ubuntu-desktop package is
installed atleast once. You may remove it after that.

---

### Post by givré on 2006-06-06
[QUOTE=web250]Metacity wasnt installed for some odd reason. Installed it and it fixed everything. Thanks![/QUOTE]
weird thing, never see that.

---

