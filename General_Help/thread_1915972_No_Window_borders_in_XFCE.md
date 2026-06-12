---
title: "No Window borders in XFCE"
date: 2012-01-27
forum: General Help
---

### Post by MaximB on 2012-01-27
Hello !

For some reason I don't have the window borders (the minimize, maximize and close bar).
In the configurations all seems fine, but it doesn't work.

I also have Gnome and KDE which don't have this issue.

Thanks
Maxim.

---

### Post by ajgreeny on 2012-01-27
Are you running compiz with your xubuntu installation?  If so try disabling it and see if that helps, or make sure the Window Decoration plugin is enabled in CCSM.

I have never used compiz in xfce so may be way out of line here, but those problems can certainly occur in gnome sometimes, so it is worth looking at as a possibility.

---

### Post by MaximB on 2012-01-27
I don't use Compiz.

---

### Post by GraeW on 2012-01-27
I saw this happen with me. Seems something caused the window manager to crash hard, so no "decorations" happened. I took the "easy way" out though and just reinstalled (I had actually been running Mint, and decided it wasn't worth the hassle, so just wiped and reinstalled Ubuntu 11.10 and XFCE).
 
Perhaps going into Synaptic, doing a complete removal and reinstall of XFCE isn't quite as drastic a solution as mine, but you might want to consider trying that unless someone else has a better idea out there?

---

### Post by Toz on 2012-01-27
No need to re-install. Simply restart the Window manager by Alt-F2 then run:
```
xfwm4 --replace
```
...or...
Reset the sessions cache:
```
rm -rf ~/.cache/sessions
```
...then logout and back in again.

Plenty of posts on this board about this issue.

---

### Post by MaximB on 2012-01-28
> **Toz said:**
> No need to re-install. Simply restart the Window manager by Alt-F2 then run:
```
xfwm4 --replace
```
...or...
Reset the sessions cache:
```
rm -rf ~/.cache/sessions
```
...then logout and back in again.

Plenty of posts on this board about this issue.

Resetting the system cache did nothing.
Replacing xfwm4 worked, but I need to do this each time I login.

Is there a permanent solution ?

---

### Post by Toz on 2012-01-28
Did you install **xfce** or **xubuntu-desktop** to an existing ubuntu or kubuntu install to get xfce? Try it this way:

Log out. Press Ctrl+Alt+F1 to go to the first TTY. Login there. Clear the sessions cache:
```
rm -rf ~/.cache/sessions
```

Ctrl+Alt+F7 to return to the GUI. Login again.

If that still doesn't work, then add:
```
xfwm4 --replace
```
...to your autostart list (Settings->Settings Manager->Session and startup->Application Autostart)

---

### Post by MaximB on 2012-01-28
> **Toz said:**
> Did you install **xfce** or **xubuntu-desktop** to an existing ubuntu or kubuntu install to get xfce? Try it this way:

Log out. Press Ctrl+Alt+F1 to go to the first TTY. Login there. Clear the sessions cache:
```
rm -rf ~/.cache/sessions
```

Ctrl+Alt+F7 to return to the GUI. Login again.

If that still doesn't work, then add:
```
xfwm4 --replace
```
...to your autostart list (Settings->Settings Manager->Session and startup->Application Autostart)

Thanks, it works now.

---

