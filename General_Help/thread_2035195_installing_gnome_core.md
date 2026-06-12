---
title: "installing gnome core"
date: 2012-07-30
forum: General Help
---

### Post by spunkycabage11 on 2012-07-30
I was trying to install gnome core so that i can later install vnc server and vnc into my server and i get this error. I'm running ubuntu 12.04

Now whenever i try to run sudo apt-get install gnome-core i get the error E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Here's the terminal session:
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done
burhan@epsilon:~$ sudo apt-get install gnome-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnustep-base-common libflite1 gnustep-base-runtime gnustep-gui-common
  libgnustep-gui0.20 plex-archive-keyring libao-common libgnustep-base1.22
  autotools-dev gnustep-common libao4 libobjc3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alacarte cups-pk-helper dconf-tools epiphany-browser epiphany-browser-data
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0
  gir1.2-gkbd-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs gnome-applets
  gnome-applets-data gnome-backgrounds gnome-contacts gnome-dictionary
  gnome-icon-theme-extras gnome-icon-theme-full gnome-js-common gnome-panel
  gnome-panel-data gnome-search-tool gnome-session-fallback gnome-shell
  gnome-shell-common gnome-themes-standard indicator-applet-complete
  indicator-messages indicator-status-provider-mc5 libcaribou-common
  libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common
  libcogl-pango0 libcogl9 libept1.4.12 libgdict-1.0-6 libgdict-common libgjs0c
  libmozjs185-1.0 libmutter0 libpanel-applet-4-0 librarian0 libseed-gtk3-0
  libvte-common libvte9 mutter-common notification-daemon rarian-compat
  synaptic
Suggested packages:
  epiphany-extensions uswsusp gnome-mag gok tomboy gnome-netstatus-applet
  deskbar-applet cpufrequtils gnome evolution desktop-base dwww menu deborphan
The following NEW packages will be installed
  alacarte cups-pk-helper dconf-tools epiphany-browser epiphany-browser-data
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0
  gir1.2-gkbd-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs gnome-applets
  gnome-applets-data gnome-backgrounds gnome-contacts gnome-core
  gnome-dictionary gnome-icon-theme-extras gnome-icon-theme-full
  gnome-js-common gnome-panel gnome-panel-data gnome-search-tool
  gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard
  indicator-applet-complete indicator-messages indicator-status-provider-mc5
  libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common
  libcogl-common libcogl-pango0 libcogl9 libept1.4.12 libgdict-1.0-6
  libgdict-common libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0
  librarian0 libseed-gtk3-0 libvte-common libvte9 mutter-common
  notification-daemon rarian-compat synaptic
0 upgraded, 67 newly installed, 0 to remove and 22 not upgraded.
Need to get 48.1 MB of archives.
After this operation, 123 MB of additional disk space will be used.
Do you want to continue [Y/n]? z
Abort.
burhan@epsilon:~$ sudo apt-get install gnome-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnustep-base-common libflite1 gnustep-base-runtime gnustep-gui-common
  libgnustep-gui0.20 plex-archive-keyring libao-common libgnustep-base1.22
  autotools-dev gnustep-common libao4 libobjc3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alacarte cups-pk-helper dconf-tools epiphany-browser epiphany-browser-data
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0
  gir1.2-gkbd-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs gnome-applets
  gnome-applets-data gnome-backgrounds gnome-contacts gnome-dictionary
  gnome-icon-theme-extras gnome-icon-theme-full gnome-js-common gnome-panel
  gnome-panel-data gnome-search-tool gnome-session-fallback gnome-shell
  gnome-shell-common gnome-themes-standard indicator-applet-complete
  indicator-messages indicator-status-provider-mc5 libcaribou-common
  libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common
  libcogl-pango0 libcogl9 libept1.4.12 libgdict-1.0-6 libgdict-common libgjs0c
  libmozjs185-1.0 libmutter0 libpanel-applet-4-0 librarian0 libseed-gtk3-0
  libvte-common libvte9 mutter-common notification-daemon rarian-compat
  synaptic
Suggested packages:
  epiphany-extensions uswsusp gnome-mag gok tomboy gnome-netstatus-applet
  deskbar-applet cpufrequtils gnome evolution desktop-base dwww menu deborphan
The following NEW packages will be installed
  alacarte cups-pk-helper dconf-tools epiphany-browser epiphany-browser-data
  fonts-cantarell gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0
  gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0
  gir1.2-gkbd-3.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-panelapplet-4.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gjs gnome-applets
  gnome-applets-data gnome-backgrounds gnome-contacts gnome-core
  gnome-dictionary gnome-icon-theme-extras gnome-icon-theme-full
  gnome-js-common gnome-panel gnome-panel-data gnome-search-tool
  gnome-session-fallback gnome-shell gnome-shell-common gnome-themes-standard
  indicator-applet-complete indicator-messages indicator-status-provider-mc5
  libcaribou-common libcaribou0 libclutter-1.0-0 libclutter-1.0-common
  libcogl-common libcogl-pango0 libcogl9 libept1.4.12 libgdict-1.0-6
  libgdict-common libgjs0c libmozjs185-1.0 libmutter0 libpanel-applet-4-0
  librarian0 libseed-gtk3-0 libvte-common libvte9 mutter-common
  notification-daemon rarian-compat synaptic
0 upgraded, 67 newly installed, 0 to remove and 22 not upgraded.
Need to get 48.1 MB of archives.
After this operation, 123 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gdm i386 3.0.4-0ubuntu15 [1,731 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libcaribou-common all 0.4.2-1ubuntu1 [8,304 B]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libcaribou0 i386 0.4.2-1ubuntu1 [47.3 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libcogl9 i386 1.10.0-0ubuntu2 [261 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libcogl-pango0 i386 1.10.0-0ubuntu2 [16.5 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libclutter-1.0-0 i386 1.10.6-1~precise1 [548 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe alacarte all 0.13.2-2ubuntu4 [94.2 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe epiphany-browser-data all 3.4.1-0ubuntu1 [4,060 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-js-common all 0.1.2-1 [20.9 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-cogl-1.0 i386 1.10.0-0ubuntu2 [17.2 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-coglpango-1.0 i386 1.10.0-0ubuntu2 [4,548 B]
Get:12 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-clutter-1.0 i386 1.10.6-1~precise1 [147 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libseed-gtk3-0 i386 3.2.0-1ubuntu1 [174 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe epiphany-browser i386 3.4.1-0ubuntu1 [370 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe fonts-cantarell all 0.0.8-1 [76.3 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-accountsservice-1.0 i386 0.6.15-2ubuntu9.1 [4,326 B]
Get:17 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gir1.2-caribou-1.0 i386 0.4.2-1ubuntu1 [6,092 B]
Get:18 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-gee-1.0 i386 0.6.4-1 [15.3 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-folks-0.6 i386 0.6.8-2 [16.0 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-gconf-2.0 i386 3.2.5-0ubuntu2 [7,092 B]
Get:21 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-gdesktopenums-3.0 i386 3.4.1-0ubuntu1 [7,348 B]
Get:22 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libmozjs185-1.0 i386 1.8.5-1.0.0-0ubuntu8 [1,344 kB]
Get:23 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libgjs0c i386 1.32.0-1ubuntu1 [227 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gir1.2-gjsdbus-1.0 i386 1.32.0-1ubuntu1 [4,280 B]
Get:25 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-gkbd-3.0 i386 3.4.0.2-1 [7,318 B]
Get:26 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe mutter-common all 3.4.1-0ubuntu1 [1,312 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libmutter0 i386 3.4.1-0ubuntu1 [392 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gir1.2-mutter-3.0 i386 3.4.1-0ubuntu1 [21.2 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-networkmanager-1.0 i386 0.9.4.0-0ubuntu4.1 [43.4 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe libpanel-applet-4-0 i386 1:3.4.1-0ubuntu1.1 [94.1 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe gir1.2-panelapplet-4.0 i386 1:3.4.1-0ubuntu1.1 [5,044 B]
Get:32 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-polkit-1.0 i386 0.104-1ubuntu1 [8,132 B]
Get:33 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-telepathyglib-0.12 i386 0.18.0-1ubuntu1 [58.6 kB]
Get:34 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-telepathylogger-0.2 i386 0.4.0-0ubuntu1 [4,526 B]
Get:35 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main gir1.2-upowerglib-1.0 i386 0.9.15-3git1 [6,636 B]
Get:36 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-applets-data all 3.4.1-0ubuntu1 [5,902 kB]
Get:37 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe gnome-panel-data all 1:3.4.1-0ubuntu1.1 [2,621 kB]
Get:38 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe gnome-panel i386 1:3.4.1-0ubuntu1.1 [485 kB]
Get:39 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-applets i386 3.4.1-0ubuntu1 [174 kB]
Get:40 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-backgrounds all 3.4.1-1 [8,878 kB]
Get:41 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-contacts i386 3.4.0-1 [316 kB]
Get:42 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe dconf-tools i386 0.12.0-0ubuntu1 [77.5 kB]
Get:43 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-icon-theme-extras all 3.4.0-1 [818 kB]
Get:44 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libept1.4.12 i386 1.0.6~exp1ubuntu1 [129 kB]
Get:45 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libvte-common all 1:0.28.2-3ubuntu2 [22.8 kB]
Get:46 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libvte9 i386 1:0.28.2-3ubuntu2 [372 kB]
Get:47 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe synaptic i386 0.75.9ubuntu1 [2,405 kB]
Get:48 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main notification-daemon i386 0.7.3-1 [36.5 kB]
Get:49 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-session-fallback all 3.2.1-0ubuntu8 [3,726 B]
Get:50 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main gnome-icon-theme-full all 3.4.0-0ubuntu1.1 [8,739 kB]
Get:51 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-shell-common all 3.4.1-0ubuntu2 [1,059 kB]
Get:52 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gjs i386 1.32.0-1ubuntu1 [6,914 B]
Get:53 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-shell i386 3.4.1-0ubuntu2 [338 kB]
Get:54 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe gnome-themes-standard i386 3.4.1-0ubuntu1.1 [1,455 kB]
Get:55 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libgdict-common all 3.4.0-1 [309 kB]
Get:56 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe libgdict-1.0-6 i386 3.4.0-1 [70.5 kB]
Get:57 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-dictionary i386 3.4.0-1 [1,367 kB]
Get:58 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-search-tool i386 3.4.0-1 [814 kB]
Get:59 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe gnome-core i386 1:3.0+6ubuntu3 [4,658 B]
Get:60 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe indicator-applet-complete i386 0.5.0-0ubuntu1 [23.4 kB]
Get:61 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main indicator-messages i386 0.6.0-0ubuntu1 [69.0 kB]
Get:62 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main indicator-status-provider-mc5 i386 0.6.0-0ubuntu1 [6,206 B]
Get:63 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libclutter-1.0-common all 1.10.6-1~precise1 [69.7 kB]
Get:64 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libcogl-common all 1.10.0-0ubuntu2 [187 kB]
Get:65 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main librarian0 i386 0.8.1-5 [59.2 kB]
Get:66 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main rarian-compat i386 0.8.1-5 [104 kB]
Get:67 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe cups-pk-helper i386 0.2.1.2-1 [51.6 kB]
Fetched 48.1 MB in 20s (2,316 kB/s)                                            
Extract templates from packages: 100%
Preconfiguring packages ...
Selecting previously unselected package gdm.
(Reading database ... 205268 files and directories currently installed.)
Unpacking gdm (from .../gdm_3.0.4-0ubuntu15_i386.deb) ...
Selecting previously unselected package libcaribou-common.
Unpacking libcaribou-common (from .../libcaribou-common_0.4.2-1ubuntu1_all.deb) ...
Selecting previously unselected package libcaribou0.
Unpacking libcaribou0 (from .../libcaribou0_0.4.2-1ubuntu1_i386.deb) ...
Selecting previously unselected package libcogl9.
Unpacking libcogl9 (from .../libcogl9_1.10.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package libcogl-pango0.
Unpacking libcogl-pango0 (from .../libcogl-pango0_1.10.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package libclutter-1.0-0.
Unpacking libclutter-1.0-0 (from .../libclutter-1.0-0_1.10.6-1~precise1_i386.deb) ...
Selecting previously unselected package alacarte.
Unpacking alacarte (from .../alacarte_0.13.2-2ubuntu4_all.deb) ...
Selecting previously unselected package epiphany-browser-data.
Unpacking epiphany-browser-data (from .../epiphany-browser-data_3.4.1-0ubuntu1_all.deb) ...
Selecting previously unselected package gnome-js-common.
Unpacking gnome-js-common (from .../gnome-js-common_0.1.2-1_all.deb) ...
Selecting previously unselected package gir1.2-cogl-1.0.
Unpacking gir1.2-cogl-1.0 (from .../gir1.2-cogl-1.0_1.10.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package gir1.2-coglpango-1.0.
Unpacking gir1.2-coglpango-1.0 (from .../gir1.2-coglpango-1.0_1.10.0-0ubuntu2_i386.deb) ...
Selecting previously unselected package gir1.2-clutter-1.0.
Unpacking gir1.2-clutter-1.0 (from .../gir1.2-clutter-1.0_1.10.6-1~precise1_i386.deb) ...
Selecting previously unselected package libseed-gtk3-0.
Unpacking libseed-gtk3-0 (from .../libseed-gtk3-0_3.2.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package epiphany-browser.
Unpacking epiphany-browser (from .../epiphany-browser_3.4.1-0ubuntu1_i386.deb) ...
No diversion 'diversion of /usr/bin/epiphany by epiphany-webkit', none removed.
No diversion 'diversion of /usr/share/man/man1/epiphany.1.gz by epiphany-webkit', none removed.
Selecting previously unselected package fonts-cantarell.
Unpacking fonts-cantarell (from .../fonts-cantarell_0.0.8-1_all.deb) ...
Selecting previously unselected package gir1.2-accountsservice-1.0.
Unpacking gir1.2-accountsservice-1.0 (from .../gir1.2-accountsservice-1.0_0.6.15-2ubuntu9.1_i386.deb) ...
Selecting previously unselected package gir1.2-caribou-1.0.
Unpacking gir1.2-caribou-1.0 (from .../gir1.2-caribou-1.0_0.4.2-1ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-gee-1.0.
Unpacking gir1.2-gee-1.0 (from .../gir1.2-gee-1.0_0.6.4-1_i386.deb) ...
Selecting previously unselected package gir1.2-folks-0.6.
Unpacking gir1.2-folks-0.6 (from .../gir1.2-folks-0.6_0.6.8-2_i386.deb) ...
Selecting previously unselected package gir1.2-gconf-2.0.
Unpacking gir1.2-gconf-2.0 (from .../gir1.2-gconf-2.0_3.2.5-0ubuntu2_i386.deb) ...
Selecting previously unselected package gir1.2-gdesktopenums-3.0.
Unpacking gir1.2-gdesktopenums-3.0 (from .../gir1.2-gdesktopenums-3.0_3.4.1-0ubuntu1_i386.deb) ...
Selecting previously unselected package libmozjs185-1.0.
Unpacking libmozjs185-1.0 (from .../libmozjs185-1.0_1.8.5-1.0.0-0ubuntu8_i386.deb) ...
Selecting previously unselected package libgjs0c.
Unpacking libgjs0c (from .../libgjs0c_1.32.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-gjsdbus-1.0.
Unpacking gir1.2-gjsdbus-1.0 (from .../gir1.2-gjsdbus-1.0_1.32.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-gkbd-3.0.
Unpacking gir1.2-gkbd-3.0 (from .../gir1.2-gkbd-3.0_3.4.0.2-1_i386.deb) ...
Selecting previously unselected package mutter-common.
Unpacking mutter-common (from .../mutter-common_3.4.1-0ubuntu1_all.deb) ...
Selecting previously unselected package libmutter0.
Unpacking libmutter0 (from .../libmutter0_3.4.1-0ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-mutter-3.0.
Unpacking gir1.2-mutter-3.0 (from .../gir1.2-mutter-3.0_3.4.1-0ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-networkmanager-1.0.
Unpacking gir1.2-networkmanager-1.0 (from .../gir1.2-networkmanager-1.0_0.9.4.0-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package libpanel-applet-4-0.
Unpacking libpanel-applet-4-0 (from .../libpanel-applet-4-0_1%3a3.4.1-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package gir1.2-panelapplet-4.0.
Unpacking gir1.2-panelapplet-4.0 (from .../gir1.2-panelapplet-4.0_1%3a3.4.1-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package gir1.2-polkit-1.0.
Unpacking gir1.2-polkit-1.0 (from .../gir1.2-polkit-1.0_0.104-1ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-telepathyglib-0.12.
Unpacking gir1.2-telepathyglib-0.12 (from .../gir1.2-telepathyglib-0.12_0.18.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-telepathylogger-0.2.
Unpacking gir1.2-telepathylogger-0.2 (from .../gir1.2-telepathylogger-0.2_0.4.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package gir1.2-upowerglib-1.0.
Unpacking gir1.2-upowerglib-1.0 (from .../gir1.2-upowerglib-1.0_0.9.15-3git1_i386.deb) ...
Selecting previously unselected package gnome-applets-data.
Unpacking gnome-applets-data (from .../gnome-applets-data_3.4.1-0ubuntu1_all.deb) ...
Selecting previously unselected package gnome-panel-data.
Unpacking gnome-panel-data (from .../gnome-panel-data_1%3a3.4.1-0ubuntu1.1_all.deb) ...
Selecting previously unselected package gnome-panel.
Unpacking gnome-panel (from .../gnome-panel_1%3a3.4.1-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package gnome-applets.
Unpacking gnome-applets (from .../gnome-applets_3.4.1-0ubuntu1_i386.deb) ...
Selecting previously unselected package gnome-backgrounds.
Unpacking gnome-backgrounds (from .../gnome-backgrounds_3.4.1-1_all.deb) ...
Selecting previously unselected package gnome-contacts.
Unpacking gnome-contacts (from .../gnome-contacts_3.4.0-1_i386.deb) ...
Selecting previously unselected package dconf-tools.
Unpacking dconf-tools (from .../dconf-tools_0.12.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package gnome-icon-theme-extras.
Unpacking gnome-icon-theme-extras (from .../gnome-icon-theme-extras_3.4.0-1_all.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_i386.deb) ...
Selecting previously unselected package libvte-common.
Unpacking libvte-common (from .../libvte-common_1%3a0.28.2-3ubuntu2_all.deb) ...
Selecting previously unselected package libvte9.
Unpacking libvte9 (from .../libvte9_1%3a0.28.2-3ubuntu2_i386.deb) ...
Selecting previously unselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.9ubuntu1_i386.deb) ...
Selecting previously unselected package notification-daemon.
Unpacking notification-daemon (from .../notification-daemon_0.7.3-1_i386.deb) ...
Selecting previously unselected package gnome-session-fallback.
Unpacking gnome-session-fallback (from .../gnome-session-fallback_3.2.1-0ubuntu8_all.deb) ...
Selecting previously unselected package gnome-icon-theme-full.
Unpacking gnome-icon-theme-full (from .../gnome-icon-theme-full_3.4.0-0ubuntu1.1_all.deb) ...
Selecting previously unselected package gnome-shell-common.
Unpacking gnome-shell-common (from .../gnome-shell-common_3.4.1-0ubuntu2_all.deb) ...
Selecting previously unselected package gjs.
Unpacking gjs (from .../gjs_1.32.0-1ubuntu1_i386.deb) ...
Selecting previously unselected package gnome-shell.
Unpacking gnome-shell (from .../gnome-shell_3.4.1-0ubuntu2_i386.deb) ...
Selecting previously unselected package gnome-themes-standard.
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.4.1-0ubuntu1.1_i386.deb) ...
Selecting previously unselected package libgdict-common.
Unpacking libgdict-common (from .../libgdict-common_3.4.0-1_all.deb) ...
Selecting previously unselected package libgdict-1.0-6.
Unpacking libgdict-1.0-6 (from .../libgdict-1.0-6_3.4.0-1_i386.deb) ...
Selecting previously unselected package gnome-dictionary.
Unpacking gnome-dictionary (from .../gnome-dictionary_3.4.0-1_i386.deb) ...
Selecting previously unselected package gnome-search-tool.
Unpacking gnome-search-tool (from .../gnome-search-tool_3.4.0-1_i386.deb) ...
Selecting previously unselected package gnome-core.
Unpacking gnome-core (from .../gnome-core_1%3a3.0+6ubuntu3_i386.deb) ...
Selecting previously unselected package indicator-applet-complete.
Unpacking indicator-applet-complete (from .../indicator-applet-complete_0.5.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package indicator-messages.
Unpacking indicator-messages (from .../indicator-messages_0.6.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package indicator-status-provider-mc5.
Unpacking indicator-status-provider-mc5 (from .../indicator-status-provider-mc5_0.6.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package libclutter-1.0-common.
Unpacking libclutter-1.0-common (from .../libclutter-1.0-common_1.10.6-1~precise1_all.deb) ...
Selecting previously unselected package libcogl-common.
Unpacking libcogl-common (from .../libcogl-common_1.10.0-0ubuntu2_all.deb) ...
Selecting previously unselected package librarian0.
Unpacking librarian0 (from .../librarian0_0.8.1-5_i386.deb) ...
Selecting previously unselected package rarian-compat.
Unpacking rarian-compat (from .../rarian-compat_0.8.1-5_i386.deb) ...
Selecting previously unselected package cups-pk-helper.
Unpacking cups-pk-helper (from .../cups-pk-helper_0.2.1.2-1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/5742: No space left on device
Processing triggers for libglib2.0-0 ...
Processing triggers for fontconfig ...
Processing triggers for gnome-icon-theme ...
gtk-update-icon-cache-3.0: Failed to write hash table
WARNING: icon cache generation failed
dpkg: unrecoverable fatal error, aborting:
 unable to flush /var/lib/dpkg/updates/tmp.i after padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
burhan@epsilon:~$ sudo apt-get remove gnome-core
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
burhan@epsilon:~$ sudo dpkh --configure -a
sudo: dpkh: command not found
burhan@epsilon:~$ sudo dpkg --configure -a
Setting up gir1.2-gee-1.0 (0.6.4-1) ...
Setting up libpanel-applet-4-0 (1:3.4.1-0ubuntu1.1) ...
Setting up libgdict-common (3.4.0-1) ...
Setting up gir1.2-gconf-2.0 (3.2.5-0ubuntu2) ...
Setting up gdm (3.0.4-0ubuntu15) ...
Adding group `gdm' (GID 126) ...
Done.
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 117) ...
Adding new user `gdm' (UID 117) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/gdm' does not belong to the user you are currently creating.
usermod: no changes
usermod: no changes
usermod: no changes
Setting up gnome-search-tool (3.4.0-1) ...
Setting up gnome-themes-standard (3.4.1-0ubuntu1.1) ...
Setting up libgdict-1.0-6 (3.4.0-1) ...
Setting up epiphany-browser-data (3.4.1-0ubuntu1) ...
Setting up gnome-contacts (3.4.0-1) ...
Processing triggers for doc-base ...
Scrollkeeper was installed, forcing re-registration of all documents.
Unregistering 29 doc-base files, Re-registering 29 doc-base files...
Registering documents with scrollkeeper...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up gir1.2-networkmanager-1.0 (0.9.4.0-0ubuntu4.1) ...
Setting up gnome-dictionary (3.4.0-1) ...
Setting up dconf-tools (0.12.0-0ubuntu1) ...
Setting up gnome-js-common (0.1.2-1) ...
Setting up gir1.2-accountsservice-1.0 (0.6.15-2ubuntu9.1) ...
Setting up libcogl-common (1.10.0-0ubuntu2) ...
Setting up alacarte (0.13.2-2ubuntu4) ...
Setting up librarian0 (0.8.1-5) ...
Setting up gnome-backgrounds (3.4.1-1) ...
Setting up fonts-cantarell (0.0.8-1) ...
Setting up libcogl9 (1.10.0-0ubuntu2) ...
Setting up libcaribou-common (0.4.2-1ubuntu1) ...
Setting up libvte-common (1:0.28.2-3ubuntu2) ...
Setting up cups-pk-helper (0.2.1.2-1) ...
Setting up mutter-common (3.4.1-0ubuntu1) ...
Setting up gnome-icon-theme-full (3.4.0-0ubuntu1.1) ...
update-alternatives: using /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg to provide /usr/share/icons/gnome/scalable/places/start-here.svg (start-here.svg) in auto mode.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/256x256/places/start-here.png because associated file /usr/share/icons/gnome/256x256/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/icons/gnome/48x48/places/start-here.png because associated file /usr/share/icons/gnome/48x48/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist.
gtk-update-icon-cache-3.0: Failed to write hash table
WARNING: icon cache generation failed
dpkg: unrecoverable fatal error, aborting:
 unable to flush /var/lib/dpkg/updates/tmp.i after padding: No space left on device
burhan@epsilon:~$ sudo apt-get install gnome-core
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by coffeecat on 2012-07-30
Duplicate here:

[http://ubuntuforums.org/showthread.php?t=2035199](http://ubuntuforums.org/showthread.php?t=2035199)

Thread closed.

---

