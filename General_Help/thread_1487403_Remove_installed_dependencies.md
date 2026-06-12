---
title: "Remove installed dependencies?"
date: 2010-05-18
forum: General Help
---

### Post by slickvguy on 2010-05-18
Last night, in a tired state, I searched for a hex editor in the USC, and chose to install a package called okteta. Only problem is...(I didn't realize until after it was too late to cancel)...it's a KDE package. Since it was probably one of the first (only?) KDE based app on this fresh Lucid installation, I believe about 115 (!) packages (see the list below) were installed in addition to the one I wanted. Grrrr.

I then went into synaptic and removed okteta, but as I should have known, it did not remove any of the dependencies.

I then looked at the dpkg logfile to see what had been installed. Here's what I found:

> 2010-05-18 02:27:56 install libqtcore4 <none> 4:4.6.2-0ubuntu5
2010-05-18 02:27:58 install libattica0 <none> 0.1.3-0ubuntu1
2010-05-18 02:27:58 install libqt4-network <none> 4:4.6.2-0ubuntu5
2010-05-18 02:27:58 install libqt4-xml <none> 4:4.6.2-0ubuntu5
2010-05-18 02:27:59 install libaudio2 <none> 1.9.2-3
2010-05-18 02:27:59 install libqt4-dbus <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:00 install libmng1 <none> 1.0.9-1ubuntu1
2010-05-18 02:28:00 install libqtgui4 <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:01 install libdbusmenu-qt2 <none> 0.3.2-0ubuntu1
2010-05-18 02:28:02 install libqt4-designer <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:02 install libqt4-script <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:03 install libphonon4 <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:04 install libpolkit-qt-1-0 <none> 0.95.1-1fakesync1
2010-05-18 02:28:04 install libqt4-sql <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:05 install libqt4-qt3support <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:05 install libqt4-svg <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:06 install libqt4-webkit <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:06 install libqt4-xmlpatterns <none> 4:4.6.2-0ubuntu5
2010-05-18 02:28:08 install libclucene0ldbl <none> 0.9.21b-2
2010-05-18 02:28:08 install libiodbc2 <none> 3.52.6-4
2010-05-18 02:28:09 install soprano-daemon <none> 2.4.2+dfsg.1-0ubuntu1.1
2010-05-18 02:28:10 install libexiv2-6 <none> 0.19-1
2010-05-18 02:28:10 install libsoprano4 <none> 2.4.2+dfsg.1-0ubuntu1.1
2010-05-18 02:28:11 install libstreamanalyzer0 <none> 0.7.2-0ubuntu1
2010-05-18 02:28:11 install libstreams0 <none> 0.7.2-0ubuntu1
2010-05-18 02:28:12 install kdelibs5-data <none> 4:4.4.2-0ubuntu4
2010-05-18 02:28:56 install kdelibs-bin <none> 4:4.4.2-0ubuntu4
2010-05-18 02:28:57 install shared-desktop-ontologies <none> 0.3-1
2010-05-18 02:28:58 install kdelibs5 <none> 4:4.4.2-0ubuntu4
2010-05-18 02:29:03 install exiv2 <none> 0.19-1
2010-05-18 02:29:04 install libqca2 <none> 2.0.2-1ubuntu2
2010-05-18 02:29:04 install libqt4-opengl <none> 4:4.6.2-0ubuntu5
2010-05-18 02:29:05 install libplasma3 <none> 4:4.4.2-0ubuntu4
2010-05-18 02:29:05 install libssh-4 <none> 0.4.2-1ubuntu1
2010-05-18 02:29:06 install kdebase-runtime-data <none> 4:4.4.2-0ubuntu4
2010-05-18 02:29:40 install oxygen-icon-theme <none> 4:4.4.2-0ubuntu2
2010-05-18 02:30:27 install libmodplug0c2 <none> 1:0.8.7-1build1
2010-05-18 02:30:28 install libmpcdec3 <none> 1:1.2.2-2.1ubuntu1
2010-05-18 02:30:28 install libxine1-bin <none> 1.1.17-1ubuntu3
2010-05-18 02:30:30 install libxine1-misc-plugins <none> 1.1.17-1ubuntu3
2010-05-18 02:30:33 install libxcb-shape0 <none> 1.5-2
2010-05-18 02:30:33 install libxcb-shm0 <none> 1.5-2
2010-05-18 02:30:34 install libxcb-xv0 <none> 1.5-2
2010-05-18 02:30:34 install libxine1-x <none> 1.1.17-1ubuntu3
2010-05-18 02:30:35 install libxine1-console <none> 1.1.17-1ubuntu3
2010-05-18 02:30:35 install libxine1 <none> 1.1.17-1ubuntu3
2010-05-18 02:30:35 install phonon-backend-xine <none> 4:4.4.0-0ubuntu2
2010-05-18 02:30:36 install kdebase-runtime <none> 4:4.4.2-0ubuntu4
2010-05-18 02:30:36 install plasma-scriptengine-javascript <none> 4:4.4.2-0ubuntu4
2010-05-18 02:30:42 install libakonadiprivate1 <none> 1.3.1-0ubuntu3
2010-05-18 02:30:42 install libboost-program-options1.40.0 <none> 1.40.0-4ubuntu4
2010-05-18 02:30:43 install kdepimlibs-data <none> 4:4.4.2-0ubuntu2
2010-05-18 02:30:47 install kdepimlibs5 <none> 4:4.4.2-0ubuntu2
2010-05-18 02:30:49 install libqt4-assistant <none> 4:4.6.2-0ubuntu5
2010-05-18 02:30:49 install libqt4-help <none> 4:4.6.2-0ubuntu5
2010-05-18 02:30:49 install phonon <none> 4:4.6.2-0ubuntu5
2010-05-18 02:30:50 install libqt4-scripttools <none> 4:4.6.2-0ubuntu5
2010-05-18 02:30:51 install libqt4-test <none> 4:4.6.2-0ubuntu5
2010-05-18 02:30:51 install python-qt4 <none> 4.7.2-0ubuntu1
2010-05-18 02:30:51 install python-sip <none> 4.10.1-0ubuntu1
2010-05-18 02:30:54 install python-kde4 <none> 4:4.4.2-0ubuntu2
2010-05-18 02:30:55 install kdesudo <none> 3.4.2.3-0ubuntu1
2010-05-18 02:30:56 install gdebi-kde <none> 0.6.0ubuntu1
2010-05-18 02:30:56 install icoutils <none> 0.26.0-4ubuntu1
2010-05-18 02:30:57 install install-package <none> 0.5.2
2010-05-18 02:30:58 install libkephal4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:30:58 install libkfontinst4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:30:58 install libkscreensaver5 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:30:59 install libkworkspace4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:30:59 install libplasmagenericshell4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:30:59 install libprocesscore4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:00 install libprocessui4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:00 install libqimageblitz4 <none> 1:0.0.4-4build1
2010-05-18 02:31:00 install libsolidcontrolifaces4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:01 install libplasma-applet-system-monitor4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:01 install libplasmaclock4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:01 install libsolidcontrol4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:02 install libksgrd4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:02 install libplasma-geolocation-interface4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:02 install libtaskmanager4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:03 install libweather-ion4 <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:03 install plasma-dataengines-workspace <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:05 install mysql-common <none> 5.1.41-3ubuntu12
2010-05-18 02:31:06 install libmysqlclient16 <none> 5.1.41-3ubuntu12
2010-05-18 02:31:06 install mysql-server-core-5.1 <none> 5.1.41-3ubuntu12
2010-05-18 02:31:09 install libqt4-sql-mysql <none> 4:4.6.2-0ubuntu5
2010-05-18 02:31:09 install mysql-client-core-5.1 <none> 5.1.41-3ubuntu12
2010-05-18 02:31:10 install akonadi-server <none> 1.3.1-0ubuntu3
2010-05-18 02:31:10 install kdepim-runtime <none> 4:4.4.2-0ubuntu1
2010-05-18 02:31:14 install plasma-widgets-workspace <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:16 install kdebase-workspace-data <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:26 install kdebase-workspace-kgreet-plugins <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:26 install polkit-kde-1 <none> 0.95.1-2ubuntu1
2010-05-18 02:31:27 install kdebase-workspace-bin <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:34 install ksysguardd <none> 4:4.4.2-0ubuntu14
2010-05-18 02:31:34 install libpackagekit-qt-12 <none> 0.5.7-0ubuntu2
2010-05-18 02:31:35 install software-properties-kde <none> 0.75.10
2010-05-18 02:31:36 install libpackagekit-glib2-12 <none> 0.5.7-0ubuntu2
2010-05-18 02:31:36 install python-packagekit <none> 0.5.7-0ubuntu2
2010-05-18 02:31:37 install packagekit-backend-apt <none> 0.5.7-0ubuntu2
2010-05-18 02:31:37 install packagekit <none> 0.5.7-0ubuntu2
2010-05-18 02:31:38 install update-manager-kde <none> 1:0.134.8
2010-05-18 02:31:39 install kpackagekit <none> 0.5.4-0ubuntu4
2010-05-18 02:31:41 install kubuntu-debug-installer <none> 10.04ubuntu4
2010-05-18 02:31:41 install okteta <none> 4:4.4.2-0ubuntu1
2010-05-18 02:31:42 install ttf-dejavu-extra <none> 2.30-2
2010-05-18 02:31:43 install ttf-dejavu <none> 2.30-2
2010-05-18 02:31:44 install virtuoso-nepomuk <none> 6.1.0-0ubuntu3


I searched for the format of the logfile, and apparently the <none> field is where the installed version goes, i.e. NONE of these packages were installed beforehand.

But now when I use aptitude or whatever to simulate removing the packages that are "not needed", the list of packages it would remove contains only about half of the packages in the list above (as well as including some packages that are not in that list).

I forget the command/program, but I then looked at why it wouldn't remove a few of the packages not in that list. It listed a few lines showing relationships and the reasoning behind non-inclusion on it's remove list.

So my questions are:

1) Is it safe to remove just that list of packages that were installed when I installed okteta (i.e. the list above) since they all have <none> in the currently installed field?

2) If so, how can I do it? The autoremove list isn't what I want, so I imagine I can make a file with the names of those packages above and have it be the input into one of the package managers to select only packages in that that list for purge, and then purge them all in one shot? 

I'd really like to get rid of all those unneeded files in order to keep my installation size to a minimum (especially when I do my partition backups). Any help would be appreciated. Thank you.

---

### Post by BslBryan on 2010-05-19
It's pretty simple.  Just don't use the GUI.  Open up a terminal and just type ```
sudo apt-get remove --purge
``` followed by your packages.  A little time consuming, maybe, but if nothing was wrong with them not being installed before, it shouldn't make a difference afterwards. :)

---

### Post by Nythain on 2010-05-19
could try

sudo apt-get --purge autoremove

---

### Post by BslBryan on 2010-05-19
> **slickvguy said:**
> ...The autoremove list isn't what I want...

It was what I was thinking too, though. ;)

---

