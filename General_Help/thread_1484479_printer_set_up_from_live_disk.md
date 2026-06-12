---
title: "printer set up from live disk"
date: 2010-05-15
forum: General Help
---

### Post by eshadcloud on 2010-05-15
I have a couple of questions here first being can a printer be set up from a live disk and secondly if a printer can be set up how?

---

### Post by agnes on 2010-05-15
1. yes
2. depends on distro

More:
I assume you mean Live CD/USB?
Some distros are made to be run on Live CD's (or Live USB-sticks), for example Knoppix or Puppy. They therefore have an option in the menus, to save your settings to a file on your hard drive or USB drive. The Live CD/USB will then search for, and load, that settings file when you next boot from it. Ubuntu Live CD has no such easy built-in option. Just sayin', because you probably want your printer settings to be saved.

How to set up a printer is different per distro, but nowadays for most distros is just easily done via a menu. Underneath it involves using CUPS (common unix printing system; usually pre-installed) and if you have a HP printer, the hplip package (usually not pre-installed). Of  course it depends on the distro what exactly to do.

---

