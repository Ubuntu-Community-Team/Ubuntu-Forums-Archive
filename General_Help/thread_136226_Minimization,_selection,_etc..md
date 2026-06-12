---
title: "Minimization, selection, etc."
date: 2006-02-25
forum: General Help
---

### Post by IYY on 2006-02-25
I am running Gnome on fairly old hardware, it it's quite fast with the anti-aliasing of the fonts turned off. Some things, however, are still very slow and I want to change them:

1. I want to remove the minimize effect.
2. I don't need that fancy semi-transparent selection, a simple wireframe like in Windows 98 would be perfect.
3. Opaque window moving is also slow sometimes. I'd rather have wireframe.

As far as I know, these features were once included in Gnome, but are currently impossible to change via the GUI. Are there any config files I could change this settings in, or am I stuck with these defaults?

---

### Post by heimo on 2006-02-25
Run configuration editor (somewhere in the Applications-menu, or in terminal: gconf-editor), check /apps/metacity/general/reduced_resources. This at least changes 1 and 3.

---

### Post by IYY on 2006-02-25
Thank you! \\:D/

---

