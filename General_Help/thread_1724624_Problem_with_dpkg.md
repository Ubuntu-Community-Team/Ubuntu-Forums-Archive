---
title: "Problem with dpkg"
date: 2011-04-08
forum: General Help
---

### Post by Melanitsky on 2011-04-08
After adding the repository under gnome3 and certain magical event with apt-get the error occurred
*fopen (K40umountfs): Permission denied*

[I]# dpkg-reconfigure-a
**insserv: fopen (K40umountfs): Permission denied**
update-rc.d: error: insserv rejected the script header[/I]

In establishing the rights of even 777 /etc/rc0.d/K40umountfs error remains.
Help please.

---

### Post by Melanitsky on 2011-04-08
i have 6 broken package.

[I]Errors were encountered while processing:
 udev
 module-init-tools
 initscripts
 dbus
 gnome-bluetooth
 sane-utils[/I]

---

