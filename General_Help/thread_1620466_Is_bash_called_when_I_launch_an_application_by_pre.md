---
title: "Is bash called when I launch an application by pressing Alt+F2"
date: 2010-11-13
forum: General Help
---

### Post by adit on 2010-11-13
If I type "firefox" into terminal, at first bash is called.  Bash then calls firefox.
I press Alt+F2.  In the dialog window I type firefox.  Firefox starts. Is bash ever called during this process?  Or the gnome desktop environment directly calls firefox (without the intervention of bash)?

---

### Post by WorMzy on 2010-11-13
I can't give you a definite answer on this, since it's not something I've ever put much thought into, but I assume that it must connect to your login shell to know what your PATH variable is, so that it knows that "firefox" refers to "/usr/bin/firefox". I don't think it launches a new instance of bash for this, otherwise there'd be several instances of bash listed in top or gnome-system-monitor.

---

### Post by mike2357 on 2010-11-13
Bash does not appear to be called directly.  I tried various commands using ALT-F2, and then while they were running, opened another window and ran the "ps -fu <my_username>" command.  Other than the window I directly opened, I did not see bash listed.

---

