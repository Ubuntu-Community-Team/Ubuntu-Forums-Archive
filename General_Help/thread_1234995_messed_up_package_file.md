---
title: "messed up package file"
date: 2009-08-08
forum: General Help
---

### Post by dethtron5000 on 2009-08-08
Hi - 
While trying to update the flashplugin-installer package, my system crashed.  Now I have a messed up package that can neither be uninstalled or reinstalled.  I've tried
apt-get clean
dpkg --configure -a

to try to resolve the conflict.

here's what happens when I try to reinstall (I get the same basic error messages when I try to remove):
sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  python-reportlab python-renderpm python-qt4-dbus python-reportlab-accel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/19.2kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 209278 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.0.32.18ubuntu0.9.04.1 (using .../flashplugin-installer_10.0.32.18ubuntu0.9.04.1_amd64.deb) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/iceweasel-flashplugin corrupt: invalid update mode
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
prerm called with unknown argument `failed-upgrade'
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.0.32.18ubuntu0.9.04.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.0.32.18ubuntu0.9.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help will be appreciated

---

