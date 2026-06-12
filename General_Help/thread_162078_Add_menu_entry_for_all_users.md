---
title: "Add menu entry for all users"
date: 2006-04-18
forum: General Help
---

### Post by draraman on 2006-04-18
How can I add an entry (let's say to the Applications -> Accessories menu) such that it's visible to all users - i.e., how can i change the default menu items? i know i can copy my .config/* to each user's home path. But i've been unable to find the location of the default menu configuration.

thanks much.

---

### Post by Sutekh on 2006-04-18
The files relating to menu entires are in the /usr/share/applications/ folder.  

The files are .desktop files that determine the name/description/icon/command and menu location of a particular application.

If **<some program>.desktop** is in there, then it should be available to all users.

---

