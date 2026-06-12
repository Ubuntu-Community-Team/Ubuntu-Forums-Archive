---
title: "How to uninstall Avast Antivirus"
date: 2011-05-02
forum: General Help
---

### Post by cymbaline42 on 2011-05-02
This tutorial aims to show you how to uninstall Avast antivirus for Ubuntu.

For Windows, Avast provides a separate utility to uninstall.  However, for Ubuntu, such a utility does not exist.  I tried searching in Synaptic and Software Center for "avast" but did not find the package.

However, some friendly folks at the Ubuntu chat channel on XIRC instructed me to try opening the terminal, and typing

sudo apt-get remove avast4workstation

or 

sudo dpkg --purge avast4workstation_1.3 (replace the 1.3 with the version you are trying to uninstall)

One of these should work to remove Avast from Ubuntu.

---

### Post by mikaelcrocker on 2012-04-16
When i remove a package i typically use `sudo apt-get remove --purge (package name)` then sudo apt-get clean, which cleans up local repos of retrieved packages.  The lock file in  /var/cache/archives/ and /var/cache/archives/partial/ will still exist though

---

