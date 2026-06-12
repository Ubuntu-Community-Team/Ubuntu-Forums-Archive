---
title: "FlightGear won't start"
date: 2011-07-26
forum: General Help
---

### Post by entryname on 2011-07-26
Hello all

Can't start FlightGear. Tried reinstalling, tried uninstalling and reinstalling (both with Synaptic), still won't start.

Suggestions?

michael@Advent7072:~$ fgfs
Xlib:  extension "GLX" missing on display ":0.0".
Error: :0.0 has no GLX extension.
Xlib:  extension "GLX" missing on display ":0.0".
Error: :0.0 has no GLX extension.
Segmentation fault

michael@Advent7072:~$ locate flightgear
/home/michael/Desktop/flightgear.desktop
/usr/share/app-install/desktop/flightgear.desktop
/usr/share/app-install/icons/flightgear.xpm
/usr/share/applications/flightgear.desktop
/usr/share/doc/flightgear
/usr/share/doc/flightgear/AUTHORS
/usr/share/doc/flightgear/AptNavFAQ.FlightGear.html
/usr/share/doc/flightgear/FlightGear-FAQ.html
/usr/share/doc/flightgear/NEWS.gz
/usr/share/doc/flightgear/Nasal.html
/usr/share/doc/flightgear/README
/usr/share/doc/flightgear/README.Debian
/usr/share/doc/flightgear/README.IO.gz
/usr/share/doc/flightgear/README.JSBSim
/usr/share/doc/flightgear/README.Joystick
/usr/share/doc/flightgear/README.Linux.gz
/usr/share/doc/flightgear/README.SimGear
/usr/share/doc/flightgear/README.TerraSync
/usr/share/doc/flightgear/README.autoconf
/usr/share/doc/flightgear/README.commands.gz
/usr/share/doc/flightgear/README.conditions.gz
/usr/share/doc/flightgear/README.digitalfilters.gz
/usr/share/doc/flightgear/README.electrical.gz
/usr/share/doc/flightgear/README.extensions
/usr/share/doc/flightgear/README.fgjs
/usr/share/doc/flightgear/README.gui.gz
/usr/share/doc/flightgear/README.introduction
/usr/share/doc/flightgear/README.jsclient
/usr/share/doc/flightgear/README.logging
/usr/share/doc/flightgear/README.multiplayer.gz
/usr/share/doc/flightgear/README.plib
/usr/share/doc/flightgear/README.properties.gz
/usr/share/doc/flightgear/README.protocol.gz
/usr/share/doc/flightgear/README.running.gz
/usr/share/doc/flightgear/README.sound
/usr/share/doc/flightgear/README.src
/usr/share/doc/flightgear/README.submodels.gz
/usr/share/doc/flightgear/README.tutorial
/usr/share/doc/flightgear/README.uiuc.gz
/usr/share/doc/flightgear/README.xmlhud.gz
/usr/share/doc/flightgear/README.xmlpanel.gz
/usr/share/doc/flightgear/README.xmlsound.gz
/usr/share/doc/flightgear/README.xmlsyntax.gz
/usr/share/doc/flightgear/Thanks.gz
/usr/share/doc/flightgear/changelog.Debian.gz
/usr/share/doc/flightgear/changelog.gz
/usr/share/doc/flightgear/copyright
/usr/share/menu/flightgear
/usr/share/pixmaps/flightgear.xpm
/var/cache/apt/archives/flightgear_1.9.1-1ubuntu2_i386.deb
/var/lib/dpkg/info/flightgear.list
/var/lib/dpkg/info/flightgear.md5sums
/var/lib/dpkg/info/flightgear.postinst
/var/lib/dpkg/info/flightgear.postrm

---

### Post by TRoe on 2011-08-11
Does your video card support OpenGL? Are you using open source drivers or the proprietary drivers?
 
You also may want to check on the system requirements and the troubleshooting section here: [http://www.flightgear.org/Docs/getstart/getstart.html](http://www.flightgear.org/Docs/getstart/getstart.html)

---

