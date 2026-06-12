---
title: "problem updating"
date: 2011-12-11
forum: General Help
---

### Post by benpack101 on 2011-12-11
Could anyone explain to me this error when I apt-get upgrade?
and what I need to do to fix it?

Thanks!


benpack101: sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
18 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up unattended-upgrades (0.73ubuntu1) ...
update-rc.d: warning: unattended-upgrades start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (none)
update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 6)
Checking for running unattended-upgrades: 
Traceback (most recent call last):
  File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 27, in <module>
    import apt_pkg
ImportError: No module named apt_pkg
invoke-rc.d: initscript unattended-upgrades, action "start" failed.
dpkg: error processing unattended-upgrades (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-software-properties:
 python-software-properties depends on unattended-upgrades; however:
  Package unattended-upgrades is not configured yet.
dpkg: error processing python-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-propertiesNo apport report written because the error message indicates its a followup error from a previous failure.
                No apport report written because the error message indicates its a followup error from a previous failure.
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      -gtk:
 software-properties-gtk depends on python-software-properties; however:
  Package python-software-properties is not configured yet.
 software-properties-gtk depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python-aptdaemon (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-seNo apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  lector-gnome depends on aptdaemon (>= 0.40+bzr527); however:
  Package aptdaemon is not configured yet.
 language-selector-gnome depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing language-selector-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on apturl; however:
  Package apturl is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on aptdaemon (>= 0.40); however:
  Package aptdaemon is not configured yet.
 software-center depends on python-aptdaemon (>= 0.40); however:
  Package python-aptdaemon is not configured yet.
 software-center depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on apturl (>= 0.1.2ubuntu1) | apturl-kde; however:
  Package apturl is not configured yet.
  Package apturl-kde is not installed.
dpkg: error processing xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on xul-ext-ubufox; however:
  Package xul-ext-ubufox is not configured yet.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on language-selector-gnome; however:
  Package language-selector-gnome is not configured yet.
 ubuntu-desktop depends on software-center; however:
  Package software-center is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python-aptdaemon (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.43+bzr697-0ubuntu1); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sessioninstaller:
 sessioninstaller depends on aptdaemon (>= 0.30); however:
  Package aptdaemon is not configured yet.
 sessioninstaller depends on python-aptdaemon-gtk (>= 0.30); however:
  Package python-aptdaemon-gtk is not configured yet.
dpkg: error processing sessioninstaller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-installer:
 ubuntuone-installer depends on python-aptdaemon; however:
  Package python-aptdaemon is not configured yet.
 ubuntuone-installer depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing ubuntuone-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-control-panel-gtk:
 ubuntuone-control-panel-gtk depends on python-aptdaemon; however:
  Package python-aptdaemon is not configured yet.
 ubuntuone-control-panel-gtk depends on python-aptdaemon.gtkwidgets | python-aptdaemon-gtk; however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
  Package python-aptdaemon-gtk is not configured yet.
 ubuntuone-control-panel-gtk depends on ubuntuone-installer (>= 2.0.0); however:
  Package ubuntuone-installer is not configured yet.
dpkg: error processing ubuntuone-control-panel-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unattended-upgrades
 python-software-properties
 python-aptdaemon
 python-aptdaemon.gtk3widgets
 software-properties-gtk
 apturl
 aptdaemon
 language-selector-gnome
 nautilus-share
 software-center
 xul-ext-ubufox
 ubufox
 ubuntu-desktop
 python-aptdaemon.gtkwidgets
 python-aptdaemon-gtk
 sessioninstaller
 ubuntuone-installer
 ubuntuone-control-panel-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jerrrys on 2011-12-12
did you update before you upgrade?

---

