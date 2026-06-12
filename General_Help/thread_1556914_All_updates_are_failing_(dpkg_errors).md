---
title: "All updates are failing (dpkg errors)"
date: 2010-08-20
forum: General Help
---

### Post by TheNighthawk on 2010-08-20
Hi,
 
I hope somebody can help me with this, I've already tried dozens of things but nothing helps, just hope that reinstall won't be the last resort :-(
 
So if somebody could give me tips what to do, I would be very happy :-)
 
Thanks in advance !
 
====================================
 
koen@beite-m1:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
31 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up akonadi-server (1.3.1-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing akonadi-server (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdepim-runtime:
kdepim-runtime depends on akonadi-server; however:
Package akonadi-server is not configured yet.
dpkg: error processing kdepim-runtime (--configure):
dependency problems - leaving unconfigured
Setting up kdesudo (3.4.2.3-0ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdesudo (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libao2 (0.8.8-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libao2 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libflac++6 (1.2.1-2build2) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libflac++6 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libk3b6:
libk3b6 depends on libflac++6 (>= 1.2.1); however:
Package libflac++6 is not configured yet.
dpkg: error processing libk3b6 (--configure):
dependency problems - leaving unconfigured
Setting up libkephal4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libkephal4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libkfontinst4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libkfontinst4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libkscreensaver5 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libkscreensaver5 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libksgrd4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libksgrd4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libkworkspace4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libkworkspace4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libplasma-applet-system-monitor4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libplasma-applet-system-monitor4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libplasma-geolocation-interface4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libplasma-geolocation-interface4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libplasmaclock4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libplasmaclock4 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libplasmagenericshell4:
libplasmagenericshell4 depends on libkworkspace4 (>= 4:4.4.2); however:
Package libkworkspace4 is not configured yet.
dpkg: error processing libplasmagenericshell4 (--configure):
dependency problems - leaving unconfigured
Setting up libprocesscore4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libprocesscore4 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libprocessui4:
libprocessui4 depends on libprocesscore4 (>= 4:4.4.2); however:
Package libprocesscore4 is not configured yet.
dpkg: error processing libprocessui4 (--configure):
dependency problems - leaving unconfigured
Setting up libqimageblitz4 (1:0.0.4-4build1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqimageblitz4 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libsolidcontrolifaces4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsolidcontrolifaces4 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsolidcontrol4:
libsolidcontrol4 depends on libsolidcontrolifaces4 (>= 4:4.4.2); however:
Package libsolidcontrolifaces4 is not configured yet.
dpkg: error processing libsolidcontrol4 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtaskmanager4:
libtaskmanager4 depends on libkephal4 (>= 4:4.4.2); however:
Package libkephal4 is not configured yet.
dpkg: error processing libtaskmanager4 (--configure):
dependency problems - leaving unconfigured
Setting up libweather-ion4 (4:4.4.2-0ubuntu14) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libweather-ion4 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
plasma-dataengines-workspace depends on libksgrd4 (>= 4:4.4.2); however:
Package libksgrd4 is not configured yet.
plasma-dataengines-workspace depends on libplasma-geolocation-interface4 (>= 4:4.4.2); however:
Package libplasma-geolocation-interface4 is not configured yet.
plasma-dataengines-workspace depends on libsolidcontrol4 (>= 4:4.4.2); however:
Package libsolidcontrol4 is not configured yet.
plasma-dataengines-workspace depends on libtaskmanager4 (>= 4:4.4.2); however:
Package libtaskmanager4 is not configured yet.
plasma-dataengines-workspace depends on libweather-ion4 (>= 4:4.4.2); however:
Package libweather-ion4 is not configured yet.
dpkg: error processing plasma-dataenginNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
es-workspace (--configure):
dependency problems - leaving unconfigured
Setting up python-kde4 (4:4.4.2-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-kde4 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of cdrdao:
cdrdao depends on libao2 (>= 0.8.8); however:
Package libao2 is not configured yet.
dpkg: error processing cdrdao (--configure):
dependency problems - leaving unconfigured
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-glib2-12 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-qt-12 (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up python-packagekit (0.5.7-0ubuntu2) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-packagekit (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of packagekit-backend-apt:
packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however:
Package python-packagekit is not configured yet.
dpkg: error processing packagekit-backend-apt (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of packagekit:
packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however:
Package libpackagekit-glib2-12 is not configured yet.
packagekit depends on packagekit-backend-apt | packagekit-backend-smart; however:
Package packagekit-backend-apt is not configured yet.
Package packagekit-backend-smart is not installed.
dpkg: error processing packagekit (--configure):
dependency problems - leaving unconfiNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
gured
dpkg: dependency problems prevent configuration of python-packagekit-gtk:
python-packagekit-gtk depends on python-packagekit; however:
Package python-packagekit is not configured yet.
dpkg: error processing python-packagekit-gtk (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
akonadi-server
kdepim-runtime
kdesudo
libao2
libflac++6
libk3b6
libkephal4
libkfontinst4
libkscreensaver5
libksgrd4
libkworkspace4
libplasma-applet-system-monitor4
libplasma-geolocation-interface4
libplasmaclock4
libplasmagenericshell4
libprocesscore4
libprocessui4
libqimageblitz4
libsolidcontrolifaces4
libsolidcontrol4
libtaskmanager4
libweather-ion4
plasma-dataengines-workspace
python-kde4
cdrdao
libpackagekit-glib2-12
libpackagekit-qt-12
python-packagekit
packagekit-backend-apt
packagekit
python-packagekit-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bachstelze on 2010-08-20
There's something very wrong about your system.  Have you done something unusual with your packages recently?

---

### Post by plucky on 2010-08-20
> koen@beite-m1:~$ sudo apt-get -f upgrade

Why this command?

> Setting up akonadi-server (1.3.1-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing akonadi-server (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdepim-runtime:
kdepim-runtime depends on akonadi-server; however:
Package akonadi-server is not configured yet.
dpkg: error processing kdepim-runtime (--configure):
dependency problems - leaving unconfigured

The problem is with akonadi-server as all the others won't install because of dependency problems.

Try ```
sudo apt-get update
sudo apt-get clean
sudo apt-get -f install
```

Good Luck

---

