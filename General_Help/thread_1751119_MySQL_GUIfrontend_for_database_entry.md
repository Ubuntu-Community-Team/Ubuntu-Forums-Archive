---
title: "MySQL GUI/frontend for database entry"
date: 2011-05-06
forum: General Help
---

### Post by sbarmeier on 2011-05-06
When looking for MySQL GUI, I find many applications which provide a frontend to database management.

I am looking for a GUI for database entry, rather than database  management, approximating Glom or VFront, but Glom is buggy (and  development sluggish) and VFront difficult to get set up.

Ideally, I would have my own private (GTK, say) data entry tool, which  would look much like an HTML form, with labelled fields for the MySQL  columns, Previous/Next buttons, saving the current row and moving you  up/down to the next one, radio buttons or drop-down menus for columns  with limited entries, etc.

Of course, [Tab]-navigation and keyboard shortcuts [Ctrl]+[C], etc.,  should work as well. (Yes, that is very annoying about Glom, for  example.)

Anybody any ideas of where to get such a configurable data entry tool, or tutorials on how to make one yourself?

Many thanks,
Severin

---

### Post by DaithiF on 2011-05-06
Hi,
one option would be to point libreoffice base at a mysql backend, then use base's various in-built data entry / data-navigation features, or its form-building features for more customised views.

---

### Post by satanselbow on 2011-05-06
No point reinventing the wheel is there? **phpmyadmin** is generally considered the tool for the job ;)

---

