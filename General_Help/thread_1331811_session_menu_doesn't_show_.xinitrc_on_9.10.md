---
title: "session menu doesn't show .xinitrc on 9.10"
date: 2009-11-19
forum: General Help
---

### Post by danielgoldin on 2009-11-19
Non-programmer type here. I used xmonad under 9.04 and loaded it via an .xinitrc script. The session menu at the log-in prompt under 9.10 no longer supplies that option. I can only choose between gnome, Safe-gnome, and xterm. How do I load xmonad? Any help gratefully appreciated.

d.

---

### Post by Brandon Williams on 2009-11-21
I assume that you're referring to the Xclient session, which uses your .xsession script (not .xinitrc).

Try creating a file called /usr/share/xsession/xclient.desktop with the following content:
```
[Desktop Entry]
Encoding=UTF-8
Name=Run user's .xsession script
Comment=This session runs the user's .xsession script.
Exec=custom
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
X-Ubuntu-Gettext-Domain=gdm
```

I haven't tried this out, but a .desktop file like this is what made it work with the old gdm.

---

