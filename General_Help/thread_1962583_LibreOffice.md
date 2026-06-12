---
title: "LibreOffice"
date: 2012-04-21
forum: General Help
---

### Post by arno48 on 2012-04-21
Hello,
I am not able to install LibreOffice 3.5.2 as it conflicts with the installed package  "libreoffice-core".
How can I disinstall this libreoffice-core? 
My previous Libreoffice version was version 3.4.
Thanks for help

---

### Post by The Cog on 2012-04-21
I tend to install the libreoffice debs fromn their from the Libreoffice website as it is generally newer than what's in the distro. I always uninstall the previous version first, which you can do with the software centre (or with synaptic if you have that installed).

---

### Post by kohoutek1 on 2012-04-21
Actually, uninstallation of earlier version is required to get the latest LibreOffice to run successfully. This is because v. 3.5 is placed in the /opt/ directory rather than the /usr/ directory. Desktop integration files will continue to seek the path in /usr/ directory. If you don't remove the core package, you'll have a Start Center but no access to the applications.

The LibreOffice download site explains this and how to purge the old core package.

---

### Post by arno48 on 2012-04-21
I installed Synaptic and I succeed to remove all the old version.
Thank you very much.

---

