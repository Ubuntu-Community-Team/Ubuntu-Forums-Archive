---
title: "Unknown App"
date: 2009-12-05
forum: General Help
---

### Post by ChappyHappy on 2009-12-05
I have this unknown app running (see ss). 
When I hover my mouse over it, there's no name displayed. Clicking on it does not show any windows. The icon just bounces.
I did just update 9.10 and it asked for a restart.

What app is it?

Thanks

[[IMG]http://img190.imageshack.us/img190/9400/unknownapp.th.png[/IMG]](http://img190.imageshack.us/i/unknownapp.png/)

---

### Post by spiderbatdad on 2009-12-05
Looks like this has to do with the way you are starting cairo...it is starting before some other necessary system program (probably sleeping) but still displayed as active on your doc...it may be gnome-panel, idk. Kill the doc and restart it, you should no longer see the program.

---

