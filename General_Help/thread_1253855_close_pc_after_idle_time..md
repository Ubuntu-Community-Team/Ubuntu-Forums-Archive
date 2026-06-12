---
title: "close pc after idle time."
date: 2009-08-30
forum: General Help
---

### Post by hlekat on 2009-08-30
I am using ubuntu 9.04.

I am searching for a program that will automatically close the computer after some time ( x ) that the computer will not being used.

Thanks!

---

### Post by CatKiller on 2009-08-30
System &#8594; Preferences &#8594; Power Management &#8594; Put computer to sleep when inactive for: (some amount of time)

You can change between hibernate (suspend-to-disk) and suspend (suspend-to-RAM) as the action when that happens by setting the appropriate entry for the /apps/gnome-power-manager/actions/sleep_type_ac key in **gconf-editor**.

---

