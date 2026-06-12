---
title: "Downgrading Pidgin 1:2.7.2-1ubuntu1, help please"
date: 2010-08-10
forum: General Help
---

### Post by afrodeity on 2010-08-10
I'm trying to downgrade pidgin.

```

apt-cache showpkg pidginPackage: pidgin
Versions: 
1:2.7.2-1ubuntu1 (/var/lib/apt/lists/ppa.launchpad.net_guido-iodice_guiodiclucid_ubuntu_dists_lucid_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_guido-iodice_guiodiclucid_ubuntu_dists_lucid_main_binary-i386_Packages
                  MD5: f4f5827f623f141077c3679bd9a1c36e

1:2.7.1-1ubuntu1~pidgin1.10.04 (/var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_lucid_main_binary-i386_Packages
                  MD5: 1703d7902599dd9b708a40961291968e

1:2.6.6-1ubuntu4 (/var/lib/apt/lists/ubuntu.mirror.ac.za_ubuntu-archive_dists_lucid_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ubuntu.mirror.ac.za_ubuntu-archive_dists_lucid_main_binary-i386_Packages
                  MD5: d9368ea6327c888ae212a8a86bfaf6b3

1:2.6.1-1ubuntu0~pidgin1.9.04-moonos1 (/var/lib/apt/lists/ppa.launchpad.net_moonos-dev_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/ppa.launchpad.net_moonos-dev_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages
                  MD5: f0006ee0d344fc8c7fa3b68710af9b49


Reverse Depends: 
  pidgin-embeddedvideo,pidgin 1:3.0
  pidgin-embeddedvideo,pidgin 1:2.6
  pidgin-embeddedvideo,pidgin 1:3.0
  pidgin-blinklight,pidgin 1:3.0
  pidgin-blinklight,pidgin 1:2.7
  pidgin-blinklight,pidgin 1:3.0
  pidgin-openpgp,pidgin
  pidgin-encryption,pidgin
  pidgin-encryption,pidgin 1:2.7
  pidgin-encryption,pidgin 1:3.0
  pidgin-musictracker,pidgin 2.6
  pidgin-dev,pidgin 1:2.7.2-1ubuntu1
  pidgin-dbg,pidgin 1:2.7.2-1ubuntu1
  pidgin-data,pidgin
  libpurple0,pidgin 2.1.1-2
  libpurple0,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
  pidgin-dev,pidgin 1:2.7.1-1ubuntu1~pidgin1.10.04
  pidgin-dbg,pidgin 1:2.7.1-1ubuntu1~pidgin1.10.04
  pidgin-data,pidgin
  libpurple0,pidgin 2.1.1-2
  libpurple0,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
  pidgin-ppa,pidgin
  moonos-meta,pidgin
  moonos-lxde-edition,pidgin
  pidgin-dev,pidgin 1:2.6.1-1ubuntu0~pidgin1.9.04-moonos1
  pidgin-dbg,pidgin 1:2.6.1-1ubuntu0~pidgin1.9.04-moonos1
  pidgin-data,pidgin
  libpurple0,pidgin 1:2.1.1-2
  libpurple0,pidgin 1:2.1.1-2
  libpurple-bin,pidgin 1:2.1.1-2
  libpurple-bin,pidgin 1:2.1.1-2
  mac4lin-pidgin-themes,pidgin
  pidgin-facebookchat,pidgin 2.3.0
  skype4pidgin,pidgin 2.1.1
  gnome-do-plugins,pidgin
  lubuntu-desktop,pidgin
  xubuntu-desktop,pidgin
  pidgin-themes,pidgin
  pidgin-privacy-please,pidgin 2.5.0
  pidgin-plugin-pack,pidgin
  pidgin-plugin-pack,pidgin 1:2.6
  pidgin-plugin-pack,pidgin 1:3.0
  pidgin-otr,pidgin 1:2.6
  pidgin-otr,pidgin 1:3.0
  pidgin-nateon,pidgin 1:2.6
  pidgin-nateon,pidgin 1:3.0
  pidgin-mpris,pidgin
  pidgin-librvp,pidgin
  pidgin-lastfm,pidgin 2.4.3
  pidgin-hotkeys,pidgin 1:2.6
  pidgin-hotkeys,pidgin 1:3.0
  pidgin-guifications,pidgin 1:3.0
  pidgin-guifications,pidgin 1:2.6
  pidgin-guifications,pidgin 1:3.0
  pidgin-festival,pidgin 1:2.5
  pidgin-festival,pidgin 1:3.0
  pidgin-extprefs,pidgin 1:2.6
  pidgin-extprefs,pidgin 1:3.0
  pidgin-encryption,pidgin
  pidgin-encryption,pidgin 1:2.6
  pidgin-encryption,pidgin 1:3.0
  pidgin-bot-sentry,pidgin 1:2.0
  pidgin-blinklight,pidgin 1:2.4
  pidgin-blinklight,pidgin 1:3.0
  pidgin-awayonlock,pidgin
  pidgin-audacious,pidgin
  gnome-osd,pidgin
  gnome-do-plugins,pidgin
  gfire,pidgin 1:2.5.0
  ezgo-network,pidgin
  brdesktop-gnome,pidgin
  pidgin-libnotify,pidgin 1:2.6
  pidgin-libnotify,pidgin 1:3.0
  pidgin-dev,pidgin 1:2.6.6-1ubuntu4
  pidgin-dbg,pidgin 1:2.6.6-1ubuntu4
  pidgin-data,pidgin
  nautilus-sendto,pidgin 2.0.0
  libpurple0,pidgin 2.1.1-2
  libpurple0,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
  libpurple-bin,pidgin 2.1.1-2
Dependencies: 
1:2.7.2-1ubuntu1 - pidgin-data (2 1:2.7.2) pidgin-data (3 1:2.7.2-z) libatk1.0-0 (2 1.29.3) libc6 (2 2.7) libcairo2 (2 1.2.4) libdbus-1-3 (2 1.0.2) libdbus-glib-1-2 (2 0.78) libfontconfig1 (2 2.8.0) libfreetype6 (2 2.2.1) libglib2.0-0 (2 2.24.0) libgstreamer0.10-0 (2 0.10.10) libgtk2.0-0 (2 2.18.0) libgtkspell0 (2 2.0.10) libice6 (2 1:1.0.0) liblaunchpad-integration1 (2 0.1.17) libpango1.0-0 (2 1.18.0) libpurple0 (2 1:2.7.0) libsm6 (0 (null)) libstartup-notification0 (2 0.10) libx11-6 (2 0) libxml2 (2 2.6.27) libxss1 (0 (null)) gconf2 (2 2.10.1-2) perl (2 5.10.1-8ubuntu2) perlapi-5.10.1 (0 (null)) gnome-panel (18 2.1) kdebase-workspace-bin (16 (null)) docker (0 (null)) evolution-data-server (2 1.10.0) libsqlite3-0 (2 3.6.22) gstreamer0.10-plugins-base (0 (null)) gstreamer0.10-plugins-good (0 (null)) pidgin-libnotify (0 (null)) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) 
1:2.7.1-1ubuntu1~pidgin1.10.04 - pidgin-data (2 1:2.7.1) pidgin-data (3 1:2.7.1-z) libatk1.0-0 (2 1.29.3) libc6 (2 2.7) libcairo2 (2 1.2.4) libdbus-1-3 (2 1.0.2) libdbus-glib-1-2 (2 0.78) libfontconfig1 (2 2.8.0) libfreetype6 (2 2.2.1) libglib2.0-0 (2 2.23.5) libgstreamer0.10-0 (2 0.10.10) libgtk2.0-0 (2 2.18.0) libgtkspell0 (2 2.0.10) libice6 (2 1:1.0.0) liblaunchpad-integration1 (2 0.1.17) libpango1.0-0 (2 1.18.0) libpurple0 (2 2.7.0) libsm6 (0 (null)) libstartup-notification0 (2 0.10) libx11-6 (2 0) libxml2 (2 2.6.27) libxss1 (0 (null)) gconf2 (2 2.10.1-2) perl (2 5.10.1-8ubuntu2) perlapi-5.10.1 (0 (null)) gnome-panel (18 2.1) kdebase-workspace-bin (16 (null)) docker (0 (null)) evolution-data-server (2 1.10.0) libsqlite3-0 (2 3.6.22) gstreamer0.10-plugins-base (0 (null)) gstreamer0.10-plugins-good (0 (null)) pidgin-libnotify (0 (null)) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) 
1:2.6.6-1ubuntu4 - pidgin-data (2 1:2.6.6) pidgin-data (3 1:2.6.6-z) libatk1.0-0 (2 1.29.3) libc6 (2 2.7) libcairo2 (2 1.2.4) libdbus-1-3 (2 1.0.2) libdbus-glib-1-2 (2 0.78) libfontconfig1 (2 2.8.0) libfreetype6 (2 2.2.1) libglib2.0-0 (2 2.23.5) libgstreamer0.10-0 (2 0.10.10) libgtk2.0-0 (2 2.18.0) libgtkspell0 (2 2.0.10) libice6 (2 1:1.0.0) liblaunchpad-integration1 (2 0.1.17) libpango1.0-0 (2 1.18.0) libpurple0 (2 1:2.6.0) libsm6 (0 (null)) libstartup-notification0 (2 0.10) libx11-6 (2 0) libxml2 (2 2.6.27) libxss1 (0 (null)) gconf2 (2 2.10.1-2) perl (2 5.10.1-8ubuntu1) perlapi-5.10.1 (0 (null)) gnome-panel (18 2.1) kdebase-workspace-bin (16 (null)) docker (0 (null)) evolution-data-server (2 1.10.0) libsqlite3-0 (2 3.6.22) gstreamer0.10-plugins-base (0 (null)) gstreamer0.10-plugins-good (0 (null)) pidgin-libnotify (0 (null)) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 2.4.0-1) 
1:2.6.1-1ubuntu0~pidgin1.9.04-moonos1 - pidgin-data (2 1:2.6.1-1ubuntu0~pidgin1.9.04) pidgin-data (3 1:2.6.1-1ubuntu0~pidgin1.9.04-z) libatk1.0-0 (2 1.20.0) libc6 (2 2.4) libcairo2 (2 1.2.4) libdbus-1-3 (2 1.0.2) libdbus-glib-1-2 (2 0.78) libfontconfig1 (2 2.4.0) libfreetype6 (2 2.2.1) libglib2.0-0 (2 2.16.0) libgstreamer0.10-0 (2 0.10.10) libgtk2.0-0 (2 2.16.0) libgtkspell0 (2 2.0.10) libice6 (2 1:1.0.0) liblaunchpad-integration1 (2 0.1.17) libpango1.0-0 (2 1.14.0) libpurple0 (2 1:2.6.0) libsm6 (0 (null)) libstartup-notification0 (2 0.8-1) libx11-6 (0 (null)) libxss1 (0 (null)) zlib1g (2 1:1.1.4) gconf2 (2 2.10.1-2) perl (2 5.10.0-19ubuntu1.1) perlapi-5.10.0 (0 (null)) gnome-panel (18 2.1) kdebase-workspace-bin (16 (null)) docker (0 (null)) evolution-data-server (2 1.10.0) libsqlite3-0 (2 3.6.10) gstreamer0.10-plugins-base (0 (null)) gstreamer0.10-plugins-good (0 (null)) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 1:2.4.0-1) gaim (3 1:2.0.0+beta6-3) pidgin-data (3 1:2.4.0-1) 
Provides: 
1:2.7.2-1ubuntu1 - 
1:2.7.1-1ubuntu1~pidgin1.10.04 - 
1:2.6.6-1ubuntu4 - 
1:2.6.1-1ubuntu0~pidgin1.9.04-moonos1 - 
Reverse Provides: 

```


```

sudo aptitude install pidgin 1:2.7.1-1ubuntu1~pidgin1.10.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Unknown priority idgin1.10.04
E: Unknown priority idgin1.10.04
No packages will be installed, upgraded, or removed

```

What am I forgetting? Is there something I am leaving out?

---

### Post by auxbuss on 2010-09-06
The package name is wrong. The error msg is the clue:

```
  E: Unknown priority idgin1.10.04 
```

It's taking 

```
~pidgin1.10.04
```

To be the -p parameter (priority) and what follows as the priority argument. So it fails.

---

### Post by penguinv on 2010-11-01
Downgrading?  I'd like to know why? What are the differences between 2.6.6 and 2.7.4 that you dont like? Or has it failed.

Thanks.
--
Ubuntu 10.04 on an old Dell. It works.

---

### Post by afrodeity on 2010-11-03
Pidgin often suffers from regressions.One version decided to leave out a proxy notification protocol. It seems to be fine now, problem was resolved and merrily upgrading.

---

