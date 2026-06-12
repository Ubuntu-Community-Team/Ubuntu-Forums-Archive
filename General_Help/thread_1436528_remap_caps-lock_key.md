---
title: "remap caps-lock key"
date: 2010-03-22
forum: General Help
---

### Post by ajs on 2010-03-22
Hi.

On my Asus eee 1005HA I've been trying to remap the  "Caps Lock" key to something useful like "<, >, |".
I've created a .Xmodmap file in my home directory where I disable caps lock and add the modifier. It looks something like this:
```
clear lock
keycode 66 = less greater less greater bar brokenbar
``` But I never seem to get the '|' characters (bar or brokenbar) ,only '<' or '>'. If I do the same for keycode 52 (Z), all the characters appear as normal (<, >,|). For some reason or other the right Alt key (AltGr) doesn't work with the Caps Lock key.
Does anyone know if this mapping of the Caps Lock key is possible at all?

Thanks in advance.

---

