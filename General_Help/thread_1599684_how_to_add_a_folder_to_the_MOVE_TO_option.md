---
title: "how to add a folder to the MOVE TO option"
date: 2010-10-18
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-18
when i select some files and right click them i can chose the MOVE TO option to move it to either the HOME FOLDER or DESKTOP. How can I add a folder to move to?

---

### Post by Vaphell on 2010-10-18
install nautilus-actions, it should appear in system->prefs
create an item, name it 'Move to whatever' and use command 'mv %f /my/custom/folder'
%f is the shortcut for selected files iirc (help is there)
if it's valid, the option will show up after nautilus restart.

unfortunately custom actions can't be positioned manually in context menu so your 'move to ...' won't show next to 'desktop' and 'home' but in custom stuff section.

---

