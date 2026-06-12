---
title: "Software Centre"
date: 2010-08-26
forum: General Help
---

### Post by Kmob810 on 2010-08-26
I am having problems with Ubuntu Software Centre and was advised to do apt-get autoremove. The result is below. Can anyone help with this?


Do you want to continue [Y/n]? y
(Reading database ... 165846 files and directories currently installed.)
Removing libgnomedesktop2.20-cil ...
Removing libgnomedesktop2.20-cil from Mono
Removing libmono-getoptions2.0-cil ...
Removing libnotify0.4-cil ...
Removing libnotify0.4-cil from Mono
Removing librsvg2-2.18-cil ...
Removing librsvg2-2.18-cil from Mono
Removing libwnck2.20-cil ...
Removing libwnck2.20-cil from Mono
Setting up software-center (2.0.7) ...
file does not exist: /usr/share/software-center/softwarecenter/apt/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/db/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/__init__.py
file does not exist: /usr/share/software-center/softwarecenter/view/widgets/__init__.py
pycentral: pycentral pkginstall: error byte-compiling files (50)
pycentral pkginstall: error byte-compiling files (50)
dpkg: error processing software-center (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@kevin-laptop:~$

---

### Post by chaosx9 on 2010-08-27
[http://www.linuxforums.org/forum/debian-linux-help/133537-subprocess-usr-bin-dpkg-returned-error-code-1-a.html](http://www.linuxforums.org/forum/debian-linux-help/133537-subprocess-usr-bin-dpkg-returned-error-code-1-a.html)

That should help, just be careful

---

