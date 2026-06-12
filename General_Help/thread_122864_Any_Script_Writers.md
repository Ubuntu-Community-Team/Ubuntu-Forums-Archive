---
title: "Any Script Writers?"
date: 2006-01-28
forum: General Help
---

### Post by PhogHawk on 2006-01-28
Does anyone know a program that will take a screenshot and automatically upload it to an FTP server? If not, can anyone write a script for me that does so? Thank you much!

---

### Post by moephan on 2006-01-29
If there is no such program, why not try this yourself? This should be pretty easily doable to learn to do in python.

1. Start here:
[http://diveintopython.org/](http://diveintopython.org/)

2. You can see if the screen shot apps have python bindings, if not, you could always call them via the command line from a python script (gnome-panel-screenshot --window --delay 5)

3. The python library includes FTP support:
[http://www.python.org/doc/current/lib/lib.html](http://www.python.org/doc/current/lib/lib.html)

Cheers, Rick

---

