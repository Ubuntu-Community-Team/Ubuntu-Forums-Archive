---
title: "Suspend From Command Line"
date: 2011-09-10
forum: General Help
---

### Post by steevven1 on 2011-09-10
I'd like to create a keyboard shortcut for "Suspend." To do so, I'd need a way to suspend from the command line, preferably without requiring root priveleges, but if the only way is with root access, I'll just set up the sudoers file so it works with no password.

Thanks.

---

### Post by AlphaLexman on 2011-09-10
Take a look at one of the power management utilities...
```
man pm-suspend
```
Although I don't know any exact code to give you.
If it is not installed by default the package is 'pm-utils'

---

### Post by Toz on 2011-09-10
Try using dbus - you won't need elevated privledges.

```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

---

### Post by steevven1 on 2011-09-10
> **Toz said:**
> Try using dbus - you won't need elevated privledges.

```
dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

This worked like a charm. I added a lock screen command in front so that the screen would be locked before suspending so my final code was:

```
xflock4;dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

Note: This lock screen command only works for Xfce (Xubuntu). In GNOME, it would be gnome-screensaver-command -l.

---

