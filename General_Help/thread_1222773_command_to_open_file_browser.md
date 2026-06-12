---
title: "command to open file browser?"
date: 2009-07-25
forum: General Help
---

### Post by m4lte on 2009-07-25
Hey,
I want to have a short cut to open a file browser (nautilus).

I'm using compiz which offers the possibilty to bind custom commands to keyboard or mouse shortcuts. However, I'm not sure what command to use to invoke nautilus.

I have tried *nautilus --browser*, which works fine when I type it in the terminal but not when set in compiz. Other commands (e.g. */etc/acpi/screenblank.sh*) work from within compiz.
[B]How can I start nautilus using compiz?
[/B]

---

### Post by VCoolio on 2009-07-25
try this:
nautilus --no-desktop /home/username

---

### Post by m4lte on 2009-07-26
> **VCoolio said:**
> try this:
nautilus --no-desktop /home/username

that works. Thanks a lot!!

---

