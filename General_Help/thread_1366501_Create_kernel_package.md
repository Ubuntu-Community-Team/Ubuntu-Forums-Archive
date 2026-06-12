---
title: "Create kernel package"
date: 2009-12-28
forum: General Help
---

### Post by gs42 on 2009-12-28
Hi,
 i use the following command to compile a kernel from source and build kernel package:  „fakeroot make-kpkg buildpackage –initrd --revision 2009 --append-to-version -amilo“.
 If I use ubuntu kernel sources everything works fine, but if I use other kernel sources I get the following error:
 *... FATAL: Could not open 'System.map': No such file or directory make**[[2]]("http://forum.ubuntuusers.de/topic/kernelpackage-erzeugen/#source-2")**: [debian/stamp/install/linux-image-2.6.31.4-amilo-amd64-xen] Fehler 1 (ignoriert) test ! -f System.map || cp System.map \ /usr/src/linux-2.6.31.4-xen-r4/debian/linux-image-2.6.31.4-amilo-amd64-xen//boot/System.map-2.6.31.4-amilo-amd64-xen; test ! -f System.map || chmod 644 \ /usr/src/linux-2.6.31.4-xen-r4/debian/linux-image-2.6.31.4-amilo-amd64-xen//boot/System.map-2.6.31.4-amilo-amd64-xen; cp arch/x86/boot/bzImage /usr/src/linux-2.6.31.4-xen-r4/debian/linux-image-2.6.31.4-amilo-amd64-xen//boot/vmlinuz-2.6.31.4-amilo-amd64-xen cp: Aufruf von stat für „arch/x86/boot/bzImage“ nicht möglich: No such file or directory make**[[2]]("http://forum.ubuntuusers.de/topic/kernelpackage-erzeugen/#source-2")**: *** [debian/stamp/install/linux-image-2.6.31.4-amilo-amd64-xen] Fehler 1 make**[[2]]("http://forum.ubuntuusers.de/topic/kernelpackage-erzeugen/#source-2")**: Verlasse Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' make**[[1]]("http://forum.ubuntuusers.de/topic/kernelpackage-erzeugen/#source-1")**: *** [debian/stamp/do-install-arch] Fehler 2 make**[[1]]("http://forum.ubuntuusers.de/topic/kernelpackage-erzeugen/#source-1")**: Verlasse Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' dpkg-buildpackage: Fehler: debian/rules binary gab Fehler-Exitstatus 2 make: *** [debian/stamp/build/buildpackage] Fehler 2*
 

 With „make“ and „make install“ I can compile and install the kernel. So compiling should not be the problem? I tried run the „make-kpkg buildpackage ...“ command after run make. Then I get the next error:
 *ldpackage ====== making target debian/stamp/build/buildpackage ") > scripts/package/Makefile) dpkg-buildpackage -nc \ -m"Unknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf>" -k"Unknown Kernel Package Maintainer" dpkg-buildpackage: setze CFLAGS auf Standardwert: -g -O2 dpkg-buildpackage: setze CPPFLAGS auf Standardwert: dpkg-buildpackage: setze LDFLAGS auf Standardwert: -Wl,-Bsymbolic-functions dpkg-buildpackage: setze FFLAGS auf Standardwert: -g -O2 dpkg-buildpackage: setze CXXFLAGS auf Standardwert: -g -O2 dpkg-buildpackage: Quellpaket linux-source-2.6.31.4-amilo-amd64-xen dpkg-buildpackage: Quellversion 15112009 dpkg-buildpackage: Host-Architektur amd64 debian/rules build make[1: Betrete Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' ====== making target build Verlasse Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' debian/rules binary make[1: Betrete Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' ====== making target binary Verlasse Verzeichnis '/usr/src/linux-2.6.31.4-xen-r4' dpkg-genchanges -b -mUnknown Kernel Package Maintainer <unknown@unconfigured.in.etc.kernel-pkg.conf> >../linux-source-2.6.31.4-amilo-amd64-xen_15112009_amd64.changes dpkg-genchanges: Fehler: kann Dateienliste-Datei nicht lesen: No such file or directory dpkg-buildpackage: Fehler: dpkg-genchanges gab Fehler-Exitstatus 2 make: *** [debian/stamp/build/buildpackage Fehler 2*

---

### Post by gsmanners on 2009-12-28
It's a little old (2005), but you should try this guide:

[http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065)

---

