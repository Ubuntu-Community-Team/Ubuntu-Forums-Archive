---
title: "How to get the editable folder address"
date: 2011-03-12
forum: General Help
---

### Post by JigglyWiggly_ on 2011-03-12
I have been using the older Ubuntu's where the folder address is shown in the plain text.

Now in Ubuntu 10.10 the folder address is a series of buttons, which is super inconvenient.

How can I go back?

---

### Post by Krytarik on 2011-03-13
- press Alt+F2
- enter "gconf-editor"
- browse down to "/apps/nautilus/preferences/always_use_location_entry"
- tick it

To do the same to root's Nautilus, run "gksudo gconf-editor" instead.

Greetings.

---

### Post by coldraven on 2011-03-13
I just press Ctrl+L to toggle the path view then Ctrl+C to copy it.

---

