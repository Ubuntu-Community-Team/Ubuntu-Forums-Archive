---
title: "Vista XDMCP problem with Xming"
date: 2009-11-01
forum: General Help
---

### Post by WesLee on 2009-11-01
Hello,
 
I'm new to Ubuntu and I try to setup a remote desktop connection from my laptop with Vista to Ubuntu (9.10). 
 
I already visited the Xming website and tried different Google searches, but without result.
 
This is what I have done:
 
-disabled IPv6
-added [Xdmcp] Enable=true to /etc/gdm/custom.conf and to /etc/kde4/kdm/kdmrc
-allowed incoming connection 177 and 6000-6015
-allowed outgoing connections 6000-6015
-configured the Xaccess file correctly in KDE but not in GDM
 
I couldn't find Xaccess or any other file where the options can be set in GDM.
 
At this point I am able to connect to the server and log-in to KDE, but when I try to log-in to GDM and everything is loaded (I can see the desktop and the menu bars)
Xming suddenly stops working and is not responding anymore.
 
Please go easy on me, because I'm a newby.
 
Kind regards,
 
WesLee

---

