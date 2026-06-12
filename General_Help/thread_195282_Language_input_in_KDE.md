---
title: "Language input in KDE"
date: 2006-06-12
forum: General Help
---

### Post by detyabozhye on 2006-06-12
For some reason, I can't swith my keyboard input language in KDE. I have Russian Phonetic installed in both xorg.conf and in KDE, and I have the xkb options to switch languages enabled in both xorg.conf and in KDE. But it still doesn't work to switch input languages in KDE, it works fine in Gnome, Xfce, Enlightenment, Fluxbox, whatever. The language switcher thingy that should be in the panel is also missing. How can I make it do language switching in KDE?

---

### Post by detyabozhye on 2006-06-12
OK, I figured out part of it, but why can't I get xkb options to work in KDE?
Here's my keyboard xorg.conf part:
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc104"
    Option         "XkbModel" "compaqik18"
    Option         "XkbLayout" "us, ru(phonetic)"
    Option         "XkbOptions" "grp:rwin_toggle"
EndSection

```
None of the Xkb settings in System Settings->Regional and Accessability->Keyboard Layout->Xkb Options have any effect and neither do the xorg.conf settings.

---

