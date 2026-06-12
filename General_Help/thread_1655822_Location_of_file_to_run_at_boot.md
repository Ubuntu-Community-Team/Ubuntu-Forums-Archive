---
title: "Location of file to run at boot"
date: 2010-12-30
forum: General Help
---

### Post by Cogizio on 2010-12-30
How would I edit, from Terminal, the programs that run at boot?  I'm making a project that's actually kind of cool and I need to add a program and remove a program, all without using a GUI.

---

### Post by dasan on 2010-12-30
put your program or link in ~/.[kde or gnome]/autostart

---

### Post by sisco311 on 2010-12-30
Do you mean applications that start during the startup of a desktop environment (after login)?
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

Or tasks and services that start during the boot process?
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

