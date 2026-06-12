---
title: "Google Gadgets"
date: 2010-04-22
forum: General Help
---

### Post by shadowfax1 on 2010-04-22
Does anyone know the terminal commands to keep google gadgets on the desktop even after rebooting.  This is a package from synaptic.  Apparently if you 'make install' it works
just not sure how you do that?  Running 10.4 Beta2 (Bye the way Awesome program!)
Thanxs

---

### Post by labinnsw on 2010-04-25
Go to System >> Preferences >> Startup Applications
Click on Add
In the command window, type ```
/usr/bin/ggl-gtk %F
```
Give it a name. The default is "Google Gadgets (GTK)"
Adding a comment is optional. The default is "Run Google Gadgets in GNOME/GTK environment"

---

