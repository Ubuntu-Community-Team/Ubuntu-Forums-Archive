---
title: "Cups update remove??"
date: 2010-06-28
forum: General Help
---

### Post by spiky001 on 2010-06-28
Hi when the update manager is due I get alot of updates for Cups, is there a way to stop these as I dont have a printer I dont want to untick them every time what do I need to remove or is it not advised to do that

---

### Post by spiky001 on 2010-06-30
bump

---

### Post by tgalati4 on 2010-06-30
If you don't have a printer, then you can simply remove cups.  Open a terminal:

sudo apt-get remove cups

If you want to keep cups (because you might need to print at a friend's house or on vacation, etc), then you can "pin" the package at it's current status.

Open synaptic-->Package-->Lock version.  That will hold back CUPS from further updates.

---

