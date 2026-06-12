---
title: "Repair package catalogue?"
date: 2011-05-16
forum: General Help
---

### Post by Jordii on 2011-05-16
Ubuntu Software Centers requires a package catalogue repair in order to function properly, but during this repair, an error message appears:> Package operation failed
The installation or removal of a software package failed.
Details
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 196043 files and directories currently installed.) 
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb (--unpack): 
 trying to overwrite '/usr/share/icons/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build2 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb 
dpkg: dependency problems prevent configuration of gnome-shell: 
 gnome-shell depends on gnome-themes-standard (>= 2.91); however: 
  Package gnome-themes-standard is not installed. 
dpkg: error processing gnome-shell (--configure): 
 dependency problems - leaving unconfigured 


What would you guys recommend me to do?

---

### Post by jerrrys on 2011-05-17
if im reading this right this is a 11.10 package

/var/cache/apt/archives/gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb

---

