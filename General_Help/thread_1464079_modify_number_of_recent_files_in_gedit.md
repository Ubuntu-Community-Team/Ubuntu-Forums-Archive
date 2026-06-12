---
title: "modify number of recent files in gedit?"
date: 2010-04-27
forum: General Help
---

### Post by Viper187 on 2010-04-27
Is it possible to change the number of files that are displayed by the recent files list in gedit? Running Ubuntu 9.04x64. Gedit says it's 2.26.1

---

### Post by bwhite82 on 2010-04-27
Hit ALT+F2. In the box, type in: gconf-editor

goto apps/gedit-2/preferences/ui/recents

Change the value of "max_recents" from 5 to whatever you wish.

Lastly, have a nice day.

---

### Post by Viper187 on 2010-04-27
ahhh. thanks :)

---

