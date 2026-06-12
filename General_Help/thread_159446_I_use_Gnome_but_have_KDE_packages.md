---
title: "I use Gnome but have KDE packages?"
date: 2006-04-12
forum: General Help
---

### Post by Dr. Feelgood on 2006-04-12
I was flipping around in Synaptic and noticed that I have some KDE related packages installed.....

kdelibs4c2   --- core libraries for all KDE applications
kdelibs-bin   --- core binaries for all KDE applications
kdelibs-data  --- core shared data for all KDE applications
kviewshell  --- generic framework for viewer applications in KDE

I use GNOME not KDE... do actually need these at all?  I'd like to remove them if it won't interfere with anything.  Can I go ahead and uninstall them?

---

### Post by taurus on 2006-04-12
You probably installed some KDE apps on your system and since those apps are for KDE, they would also install the libraries so they can run in Gnome!!!  One well know KDE app is k3b...

---

### Post by Dr. Feelgood on 2006-04-12
[QUOTE=taurus]You probably installed some KDE apps on your system and since those apps are for KDE, they would also install the libraries so they can run in Gnome!!!  One well know KDE app is k3b...[/QUOTE]

Ok, so KDE apps will run in Gnome with these libraries?  I guess I'll just leave them then.  Thanks for the info.

---

### Post by az on 2006-04-12
[QUOTE=Dr. Feelgood]I was flipping around in Synaptic and noticed that I have some KDE related packages installed.....

kdelibs4c2   --- core libraries for all KDE applications
kdelibs-bin   --- core binaries for all KDE applications
kdelibs-data  --- core shared data for all KDE applications
kviewshell  --- generic framework for viewer applications in KDE

I use GNOME not KDE... do actually need these at all?  I'd like to remove them if it won't interfere with anything.  Can I go ahead and uninstall them?[/QUOTE]
Mark one of them for removal and synaptic will tell you what packages that would affect.  You will get your answer...

Yes, KDE apps run in Gnome and vice versa.  They just use their own framewors for hardware abstraction and sharing ressources and stuff.

---

### Post by taurus on 2006-04-12
[QUOTE=Dr. Feelgood]Ok, so KDE apps will run in Gnome with these libraries?  I guess I'll just leave them then.  Thanks for the info.[/QUOTE]
Yes, you can run KDE apps in Gnome and Gnome apps in KDE or both Gnome & KDE apps in Xfce4...  All you need are the right libraries and you are all set.

---

