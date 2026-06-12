---
title: "desktop disappeared"
date: 2009-06-26
forum: General Help
---

### Post by zero777zero on 2009-06-26
9.04 jaunty 32bit

this has happened a few times, i was in the process of doing something (copy+pasting this time) and the folder windows closed now all my desktop icons are missing (including mount links to external drives which i can still access). this problem solves itself when i reboot, everything is back to normal, but i'd like to find out how to avoid needing to reboot everytime this happens.

i think it happened once i xkill'd the desktop by accident once

heres a screen

[http://img522.imageshack.us/img522/2648/screenshot1j.png](http://img522.imageshack.us/img522/2648/screenshot1j.png)

---

### Post by blueridgedog on 2009-06-26
Do they re-appear when you hit CTRL + ALT + Backspace to restart the X server?

---

### Post by zero777zero on 2009-06-26
nope

also, right clicking on the desktop does not bring up the mouse menu

---

### Post by themusicalduck on 2009-06-26
Usually press Alt+F2, type in nautilus and hit return should bring your desktop back.

---

### Post by geirha on 2009-06-26
nautilus is the app that draws the desktop, and it sounds like it crashed for some reason. Do you see nautilus in system monitor, or with the command "ps -ef | grep nautilus"?

If you do, try running ```
killall nautilus
``` to kill it. Gnome will detect that it has been killed, and restart it. Hopefully it will be restarted properly.

---

### Post by zero777zero on 2009-06-26
> **themusicalduck said:**
> Usually press Alt+F2, type in nautilus and hit return should bring your desktop back.

that did it, thanks!

---

