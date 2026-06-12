---
title: "How do I add entries to the global menu (Dash)?"
date: 2012-05-07
forum: General Help
---

### Post by Paddy Landau on 2012-05-07
I know how to add, modify and delete entries to the menu (Dash). I install [alacarte]("apt:alacarte") and run it.

However, that is only for the current user.

How do I make equivalent changes to the global menu, i.e. the one shared by all users?

---

### Post by Cheesemill on 2012-05-07
The per user settings are stored in the .desktop files in ~/.local/share/applications

The global .desktop files are in /usr/share/applications/

---

### Post by Paddy Landau on 2012-05-07
I wanted to use a GUI, so I used alacarte to create the entry, then cut-and-pasted it from the local area to the shared area.

Log out -- log in -- it worked perfectly.

Thank you.

Marking as solved.

---

