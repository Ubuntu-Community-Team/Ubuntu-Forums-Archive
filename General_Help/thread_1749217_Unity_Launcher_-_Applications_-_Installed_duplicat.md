---
title: "Unity Launcher - Applications - Installed duplicates"
date: 2011-05-04
forum: General Help
---

### Post by Fraoch on 2011-05-04
I have a few duplicates in Launcher - Applications - Installed.

I know how they got there - these are ones I added myself to the menus in older Ubuntu versions.  Sometimes I moved them around and I left the old entries there, disabled.

The script which converted the menus must include all disabled options as well.

My instincts told me to right-click to remove a duplicate, but right-click does nothing.  I have a feeling there's a text file or menu somewhere that I could edit, but where?

Thanks.

---

### Post by Fraoch on 2011-05-05
Bump?

---

### Post by Spyderkid on 2011-05-05
use the kill command on unity sidebar then restart the process?

---

### Post by Fraoch on 2011-05-05
> **Spyderkid said:**
> use the kill command on unity sidebar then restart the process?

I'm not sure I understand...these are installed applications, not running at the time.  They're accessible through Launcher - Applications (the "magnifying glass" icon).

---

### Post by Crucias on 2011-05-06
Traditionally you would launch menu editor (type menu in the lens) and untick or delete entries.

The problem is in natty you can add but not remove. When i delete items in the menu editor you have to then manually find their physical counterparts and delete them (in folders suck as .local etc).

This is time consuming and only useful when uninstalling (which also doesnt remove items) because it kills all mention of that app

---

### Post by mc4man on 2011-05-06
If you created them yourself then likely they're in 
~/.local/share/applications
Just open that folder up and delete them

---

### Post by monkey4ahead on 2011-07-07
I removed all the Desktop files from ~/.local/share/applications apart from the ones I created myself.

---

### Post by Fraoch on 2011-07-14
> **monkey4ahead said:**
> I removed all the Desktop files from ~/.local/share/applications apart from the ones I created myself.

Thanks, that did the trick!

---

