---
title: "ubuntu 11.04 does nt work ubuntu software center either any DEB"
date: 2011-06-19
forum: General Help
---

### Post by gabak on 2011-06-19
hello everyone
phenom II 4gb RAM DDR3 1tb hdd NO WINDOWS. just FRESH ubuntu 11.04.
suddenly Ubuntu Software Center stop working and i decided to run fsck and it found some lost clusters. i fix it but it stil does nt work.
what can i do?
i dont hae grub i dont know why ubuntu did nt install it i dont know how to run maybe a fix bronken package.

thxs in advance


ps:any DEB does nt work either of course

---

### Post by gabak on 2011-06-26
i fix this

[http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center](http://ubuntuforums.org/showthread.php?t=1791038&highlight=software+center)

sudo apt-get -f install libreoffice-core


when there are problems with the libre office that and a little of the other link help me and now everything works

try this series:

Clean up your package installation

If you have installed and uninstalled a lot of applications, chances are your system is infected with a lot of dependencies files that you have absolutely no use for. Here are some useful commands to get rid of any partial package and remove any unused dependencies:
Cleaning up of partial package:
sudo apt-get autoclean

Cleaning up of the apt cache:
sudo apt-get clean

Cleaning up of any unused dependencies:
sudo apt-get autoremove

A good practice to avoid any left behind is to use the autoremove command whenever you want to uninstall an application.
sudo apt-get autoremove application-name

---

