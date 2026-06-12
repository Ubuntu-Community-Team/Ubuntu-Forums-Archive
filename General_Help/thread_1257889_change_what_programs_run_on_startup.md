---
title: "change what programs run on startup"
date: 2009-09-04
forum: General Help
---

### Post by pythonscript on 2009-09-04
I had installed some packages that used apache as a dependency, and ubuntu set it to run on startup. I run a command line ubuntu with icewm on top, so there's no splash screen on startup, and I can see ubuntu try to start apache but doesn't find it (because I've uninstalled it). Where is this listed in ubuntu? I'd like to control exactly what ubuntu starts (in terms of programs) at boot. Any ideas? I'd like for it to not generate an error message every time I boot my laptop. Thanks!

---

### Post by sedawk on 2009-09-04
When removing apache I think the startup script should automatically
be removed too (do not remove yourself!):
/etc/init.d/apache2

This script is not started directly, but via a lots of symbolic link
for different runlevels. For Ubuntu what you would do is to remove
the link to the apache startup script from /etc/rc2.d, /etc/rc[345].d

Then if you reboot your PC apache should not start anymore!

---

