---
title: "missing my tilde?!?!?"
date: 2006-04-12
forum: General Help
---

### Post by rattusdatorum on 2006-04-12
I tried to get some nice spanish letters (tilde + n = n with tilde) but now I don't even TILDE anymore
enabling multiple keyboard layouts just results in "cannot switch to keyboard layout bla"
changed the xorg.conf file, but it looks like it is completley ignored (did restart of X and of the whole f**king system).

read about 20-60 forum entries with similar problems
reseted to defaults

NOTHING

it would be nice, if even SOMEONE could tell me, how to get the TILDE BACK?!?!?

my xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "deadkeys"
        Option          "XkbVariant"    "apostrophe"
        Option          "XkbVariant"    "intl"
EndSection

---

### Post by rattusdatorum on 2006-04-12
Bump

---

### Post by onlysolution on 2006-07-02
I had the same problem, but when I removed Japanese keyboard mapping from the list of availible keymaps my tilde came back.  I think this is because on Japanese keyboards the tilde key is used to switch character modes, however I know on other int'l keyboards there are similar modifiers.  If you have one of those enabled, you might need to disable it to type tildes due to that conflict.

---

