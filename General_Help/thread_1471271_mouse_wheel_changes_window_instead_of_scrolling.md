---
title: "mouse wheel changes window instead of scrolling"
date: 2010-05-03
forum: General Help
---

### Post by dannykayeuk on 2010-05-03
I am used to the mouse behaviour changing depending on where I am. However, in 9.10 and earlier I moved over a list or a web page or a document and the mouse wheel scrolled the page or whatever. Having just installed 10.04 the mouse wheel changes windows or workspace and that is all it does. On top of this I cannot find how to change this behaviour. HELP!!!

My second problem is tooltips, how do I get rid of them?

---

### Post by WorMzy on 2010-05-03
Have you got compiz' Desktop Cube and Rotate Cube enabled? If so, open ccsm and make sure the bindings for Rotate Cube -> Rotate Left, and Rotate Right aren't Button4 and Button5. Image below for emphasis.

[[IMG]http://www.ubuntu-pics.de/thumb/56044/compizconfig_settings_manager_094_1KCW1J.png[/IMG]]("http://www.ubuntu-pics.de/bild/56044/compizconfig_settings_manager_094_1KCW1J.png")

---

### Post by WorMzy on 2010-05-03
For tooltips:

Open gconf-editor and browse to apps -> panel -> global -> tooltips_enabled, and set it to false (uncheck the box).

---

