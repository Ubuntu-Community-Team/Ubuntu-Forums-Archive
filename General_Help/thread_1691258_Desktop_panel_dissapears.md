---
title: "Desktop panel dissapears"
date: 2011-02-19
forum: General Help
---

### Post by Szotyori on 2011-02-19
Hy

My destktop panel disappears

please if someone know about this problem I will appreciate some help...

Kubuntu 10.04

[IMG]http://i51.tinypic.com/ouskr8.png[/IMG]

---

### Post by drdos2006 on 2011-02-19
Press ALT + F2 to run in terminal. Type : gconf-editor and ENTER.
Select /apps/panel/toplevels/top-panel_screen0, uncheck auto-hide.
OR
/apps/nautilus/preferences/start_with_xxxxx, click to toggle.

regards

---

### Post by pqwoerituytrueiwoq on 2011-02-19
is gnome-panel running?
alt+F2
gnome-panel
should stat it
that would do it for ubuntu not sure on kubuntu

---

