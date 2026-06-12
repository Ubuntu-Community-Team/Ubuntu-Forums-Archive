---
title: "removing panel shadow?"
date: 2011-05-15
forum: General Help
---

### Post by princeofnam on 2011-05-15
I've read several threads but none of the solutions work for me.  Namely replacing "any" with "!type=dock" in Windows Decorations.  Any suggestions? Currently running 11.04

---

### Post by princeofnam on 2011-05-22
Any option?

---

### Post by Habitual on 2011-05-22
Open CompizConfigSettingsManager (ccsm) and goto window decorations and add this to "shadow windows"

from any to !(class=Gnome-panel)

---

