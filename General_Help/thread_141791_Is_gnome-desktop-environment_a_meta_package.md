---
title: "Is gnome-desktop-environment a meta package?"
date: 2006-03-09
forum: General Help
---

### Post by vayu on 2006-03-09
I'm wanting to uninstall (disabling would be ok) Evolution.  When I mark it for removal in Synaptic it wants to remove gnome-desktop-environment.  I've searched and found a thousand references to ubuntu-desktop and it being a meta package and ok to remove except for dist-upgrade.  

Synaptic is trying to remove gnome-desktop-environment (not ubuntu-desktop) and won't let me unmark it.  When I look at what it includes it doesn't seem like a meta package to me.  I think it might be picking gnome-desktop-environment because I've already removed ubuntu-desktop when I removed evms.

---

### Post by Sutekh on 2006-03-09
This is the information about gnome-desktop-environment at packages.ubuntu.com

[http://packages.ubuntu.com/breezy/gnome/gnome-desktop-environment]("http://packages.ubuntu.com/breezy/gnome/gnome-desktop-environment")


It looks like a meta-package to me,  here is the list of files in the package

[http://http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-desktop-environment&version=breezy&arch=all]("http://http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-desktop-environment&version=breezy&arch=all")

as compared to something that gnome-desktop-environment depends on; gnome-volume-manager

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-volume-manager&version=breezy&arch=i386]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-volume-manager&version=breezy&arch=i386")

So gnome-desktop-environment doesn't install anything but depends on alot of other packages, and those packages actually install stuff.  Check out some more packages if you like.  The list of files is toward the end of the page where you can download the package

---

