---
title: "Shadows w/o compiz?"
date: 2010-10-19
forum: General Help
---

### Post by inso_741 on 2010-10-19
Is it possible?

---

### Post by perspectoff on 2010-10-19
The default KWindows manager (in Kubuntu's KDE) does it.

K menu -> System -> System settings -> General -> Desktop -> Desktop effects -> General -> Enable desktop effects -> All effects -> Shadow

---

### Post by hhh on 2010-10-19
Open Gconf-editor (Alt+F2, run the command gconf-editor). Navigate to apps>metacity>general, check the box for compositing_manager .

-edit- I forgot, an alternative is to install xcompmgr...
[http://urukrama.wordpress.com/openbox-guide/#Shadows](http://urukrama.wordpress.com/openbox-guide/#Shadows)
[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

---

### Post by inso_741 on 2010-10-19
> **hhh said:**
> Open Gconf-editor (Alt+F2, run the command gconf-editor). Navigate to apps>metacity>general, check the box for compositing_manager .

-edit- I forgot, an alternative is to install xcompmgr (this guide is for Openbox so you have to adjust it for Gnome)...
[http://urukrama.wordpress.com/openbox-guide/#Shadows](http://urukrama.wordpress.com/openbox-guide/#Shadows)

wow that was quick thanx!!

---

