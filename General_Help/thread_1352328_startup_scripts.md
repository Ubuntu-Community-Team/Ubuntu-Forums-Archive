---
title: "startup scripts?"
date: 2009-12-11
forum: General Help
---

### Post by blur xc on 2009-12-11
What file lists programs that startup during boot?

I've been curious for a lot of reasons, but I recently installed an APC UPS and apcupsd, and want to know for sure that it will run automatically after a fresh boot.

Thanks,
BM

---

### Post by lewisforlife on 2009-12-11
There are a couple of different places.  There are scripts that are run for different run levels.  The default run level for Ubuntu is level 2, so you can look in the /etc/rc2.d directory.  These are symbolic links to scripts in /etc/init.d that start programs.

Also, if you are running gnome you can look in System-->Preferences-->Startup Applications.

Also you can look at .bashrc, .xsession, and .xinitrc that are in your home directory.

---

