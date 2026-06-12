---
title: "no display"
date: 2006-03-30
forum: General Help
---

### Post by glpe on 2006-03-30
Help I edited file asound.conf and now I do not get a display. I used
cntl + alt + f1 to open terminal and entered sudo gedit /etc/asound.conf
and I get the following:
gedit : 7954 Gtk-Warning cannot open display
How can I edit this file without display?

---

### Post by Ramses de Norre on 2006-03-30
Use vi or nano instead of gedit, you can't run a gui without the X server.
To troubleshoot it you'll want to check /var/log/Xorg.0.log and ~/.xsession-errors

---

### Post by ajgreeny on 2006-03-30
Gedit only works through a display like gnome or kde. You will ned to use nano, vi, or something similar instead, which will bring up the file in terminal mode for editing.

---

### Post by glpe on 2006-03-30
Thanks, I am back in service!

---

