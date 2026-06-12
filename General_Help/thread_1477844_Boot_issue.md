---
title: "Boot issue"
date: 2010-05-09
forum: General Help
---

### Post by stefcep on 2010-05-09
hello All,

I'm using 9.04 and found its worked flawlessly until now.

I was installing epsxe using  a script on this forum.  When I re-booted I got a dialog box telling me that as the session lasted less than 10 seconds there might be an installation error or not enough disk space.  The error details were:

"/etc/gdm/xsession/X11/xsession :beginning session setup...
.:52libcanberra-gtk-module_add-to-gtk-modules"

52libcanberra-gtk-module_add-to-gtk-modules is a text file in /etc/X11/Xsession.d, and it reads:

 # This file is sourced by Xsession(5), not executed.

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi

export GTK_MODULES


I think this "canberra" thing is related to playing sounds and the boot sound no longer plays. 

Any advice on how to fix this would be greatly appreciated.

---

