---
title: "Ctrl+Alt+F1 not working in Ubuntu or Debian"
date: 2009-11-25
forum: General Help
---

### Post by maybeway36 on 2009-11-25
I've recently noticed that the Ctrl+Alt+F1 keyboard shortcut no longer does anything in either Ubuntu 9.10 or Debian squeeze.
I've found in Debian I can type
```
sudo chvt 1
```
to get me to the prompt. But then, Alt+F7 doesn't work and I need to type
```
sudo chvt 7
```
to get back. Could it have anything to do with my Radeon card?
(EDIT: it does work in Ubuntu after all)

---

### Post by Divider on 2009-11-25
I don't have this issue and cannot replicate it, try a different keyboard and see if you get the same result.

---

### Post by maybeway36 on 2009-11-25
It turns out it was the keyboard input. I was using a USB keyboard; when I plugged in a PS/2 one it worked fine.

---

