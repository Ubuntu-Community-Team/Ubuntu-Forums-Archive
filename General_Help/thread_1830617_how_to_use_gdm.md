---
title: "how to use gdm????"
date: 2011-08-22
forum: General Help
---

### Post by ashhab2010 on 2011-08-22
i installd gdm from the maveric backport updates but i have no clue on how to use it 
 typing gdm in the terminal gives me this error

 ** (gdm-binary:4245): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.60" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

 ** (gdm-binary:4245): WARNING **: Could not acquire name; bailing out


 what do i do??

---

### Post by garvinrick4 on 2011-08-22
You were using gdm already? Started using lightdm in 11.10. 
One at a time below.
```
sudo stop gdm
sudo start gdm
```or below both stop and restart gdm.
```
sudo /etc/init.d/gdm restart
```gdm package below:
```
Provides: x-display-manager
Description: GNOME Display Manager
 GDM provides the equivalent of a "login:" prompt for X displays: it asks for a
 login and starts X sessions. 
 
 It provides all the functionality of XDM, including XDMCP support for managing
 remote displays, and extends it with the ability to start X servers on demand. 
 
 The greeter is written using the GNOME libraries and hence looks like a GNOME
 application - even to the extent of supporting themes! 
 
 This package contains the next generation GDM, which was developed using the
 technologies on which GNOME is based.

```

---

