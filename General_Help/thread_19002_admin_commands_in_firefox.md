---
title: "admin commands in firefox"
date: 2005-03-09
forum: General Help
---

### Post by eraos on 2005-03-09
I want to follow this ([http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)) site's explanation on how to set up printing over a network to windows.  But when I do step 7 (bottom of page) and type in my password and user name this is the page that displays:

Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (Computer > System configuration > Printing).


Is there a way to enable admin commands in Firefox?  I checked through  about:config but I didn't recognize anything that might be useful.

---

### Post by Pluk on 2005-03-09
Administrative commands are disabled on the webserver itself, cupsys.

You can enable it by adding cupsys to the shadow group:

sudo adduser cupsys shadow


This allows the usr cupsys to check the passwords and you can login.

---

