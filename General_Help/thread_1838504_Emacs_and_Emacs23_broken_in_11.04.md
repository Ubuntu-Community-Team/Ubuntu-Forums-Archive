---
title: "Emacs and Emacs23 broken in 11.04"
date: 2011-09-03
forum: General Help
---

### Post by OpenJacob on 2011-09-03
Hi after installing Emacs23 Dpkg seemed not to fully configure some packages so I attempted to uninstall Emacs23 but Dpkg spits out this error:

Selecting previously deselected package emacsen-common.
(Reading database ... 345329 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu2_all.deb) ...
Selecting previously deselected package emacs-snapshot-common.
Unpacking emacs-snapshot-common (from .../emacs-snapshot-common_1%3a20090909-1_all.deb) ...
Selecting previously deselected package emacs-snapshot-bin-common.
Unpacking emacs-snapshot-bin-common (from .../emacs-snapshot-bin-common_1%3a20090909-1_amd64.deb) ...
Selecting previously deselected package emacs23-common.
Unpacking emacs23-common (from .../emacs23-common_23.2+1-7ubuntu2_all.deb) ...
Selecting previously deselected package emacs23-bin-common.
Unpacking emacs23-bin-common (from .../emacs23-bin-common_23.2+1-7ubuntu2_amd64.deb) ...
Selecting previously deselected package libanthy0.
Unpacking libanthy0 (from .../libanthy0_9100h-6ubuntu1_amd64.deb) ...
Selecting previously deselected package m17n-db.
Unpacking m17n-db (from .../m17n-db_1.6.2-1_all.deb) ...
Selecting previously deselected package m17n-contrib.
Unpacking m17n-contrib (from .../m17n-contrib_1.1.12-1_all.deb) ...
Selecting previously deselected package libm17n-0.
Unpacking libm17n-0 (from .../libm17n-0_1.6.2-3_amd64.deb) ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/sbm.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/sbm-cz.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/sbm-zh.info.gz'
Processing triggers for menu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up emacsen-common (1.4.19ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs
Setting up emacs-snapshot-common (1:20090909-1) ...
Setting up emacs-snapshot-bin-common (1:20090909-1) ...
update-alternatives: using /usr/bin/b2m.emacs-snapshot to provide /usr/bin/b2m (b2m) in auto mode.
update-alternatives: using /usr/bin/ctags.emacs-snapshot to provide /usr/bin/ctags (ctags) in auto mode.
update-alternatives: using /usr/bin/ebrowse.emacs-snapshot to provide /usr/bin/ebrowse (ebrowse) in auto mode.
update-alternatives: using /usr/bin/emacsclient.emacs-snapshot to provide /usr/bin/emacsclient (emacsclient) in auto mode.
update-alternatives: using /usr/bin/etags.emacs-snapshot to provide /usr/bin/etags (etags) in auto mode.
update-alternatives: using /usr/bin/grep-changelog.emacs-snapshot to provide /usr/bin/grep-changelog (grep-changelog) in auto mode.
update-alternatives: using /usr/bin/rcs-checkin.emacs-snapshot to provide /usr/bin/rcs-checkin (rcs-checkin) in auto mode.
Setting up emacs-snapshot (1:20090909-1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/emacs-snapshot because link group emacs is broken.
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.ffS17F
dpkg: error processing emacs-snapshot (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs23-common (23.2+1-7ubuntu2) ...
Setting up emacs23-bin-common (23.2+1-7ubuntu2) ...
update-alternatives: using /usr/bin/b2m.emacs23 to provide /usr/bin/b2m (b2m) in auto mode.
update-alternatives: using /usr/bin/ctags.emacs23 to provide /usr/bin/ctags (ctags) in auto mode.
update-alternatives: using /usr/bin/ebrowse.emacs23 to provide /usr/bin/ebrowse (ebrowse) in auto mode.
update-alternatives: using /usr/bin/emacsclient.emacs23 to provide /usr/bin/emacsclient (emacsclient) in auto mode.
update-alternatives: using /usr/bin/etags.emacs23 to provide /usr/bin/etags (etags) in auto mode.
update-alternatives: using /usr/bin/grep-changelog.emacs23 to provide /usr/bin/grep-changelog (grep-changelog) in auto mode.
update-alternatives: using /usr/bin/rcs-checkin.emacs23 to provide /usr/bin/rcs-checkin (rcs-checkin) in auto mode.
Setting up libanthy0 (9100h-6ubuntu1) ...
Setting up m17n-db (1.6.2-1) ...
Setting up m17n-contrib (1.1.12-1) ...
Setting up libm17n-0 (1.6.2-3) ...
Setting up emacs23 (23.2+1-7ubuntu2) ...
update-alternatives: using /usr/bin/emacs23-x to provide /usr/bin/emacs (emacs) in auto mode.
emacs-install emacs23
Package `global' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
emacsen-common: Handling install of emacsen flavor emacs23
emacsen-common: byte-compiling for emacs23
Wrote /etc/emacs23/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
Can't exec "/usr/lib/emacsen-common/packages/install/global": Permission denied at /usr/lib/emacsen-common/emacs-install line 27, <TSORT> line 2.
emacs-install: /usr/lib/emacsen-common/packages/install/global emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs23 (--configure):
 subprocess installed post-installation script returned error exit status 13
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 emacs-snapshot
 emacs23
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

I tried to fix the error with Aptitude and others but still it failed. After this one broke I started getting an ICEathority error aswell, I think it could be due to my installing AWM after the error occured but it could be a permission issue instead.

Any help?

---

### Post by searchfgold6789 on 2011-09-03
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by OpenJacob on 2011-09-03
That was my first thought.

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up emacs-snapshot (1:20090909-1) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.GKiwoG
dpkg: error processing emacs-snapshot (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs23 (23.2+1-7ubuntu2) ...
emacs-install emacs23
Package `global' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
emacsen-common: Handling install of emacsen flavor emacs23
emacsen-common: byte-compiling for emacs23
Wrote /etc/emacs23/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
Can't exec "/usr/lib/emacsen-common/packages/install/global": Permission denied at /usr/lib/emacsen-common/emacs-install line 27, <TSORT> line 2.
emacs-install: /usr/lib/emacsen-common/packages/install/global emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs23 (--configure):
 subprocess installed post-installation script returned error exit status 13
Errors were encountered while processing:
 emacs-snapshot
 emacs23
E: Sub-process /usr/bin/dpkg returned an error code (1)

The Dpkg command is empty.

---

### Post by OpenJacob on 2011-09-03
I have compiled a very large algorithm for fractal codeing and would rather not have to reinstall Ubuntu as the source is over 20Gigs and will take four days to compleatly compile.

I fixed one of my problems (ICEauthority)

chown gdm:gdm -R /var/lib/gdm chmod 600 /var/lib/gdm/.ICEauthority mv /home/*username*/.ICEauthority /home/*username*/.ICEauthority.old chmod 1777 /tmp
I think I need the configureation scripts for one or more packages to fix Emacs.

---

### Post by OpenJacob on 2011-09-03
I can't beelieve I missed Global. Installed Global and all is fine.

Mark as solved.

---

### Post by jimbobboy on 2012-10-17
Some of us don't know what you mean by "Install Global."

Please explain what you did, and assume ignorance on the part of your audience.
Thanks!

---

