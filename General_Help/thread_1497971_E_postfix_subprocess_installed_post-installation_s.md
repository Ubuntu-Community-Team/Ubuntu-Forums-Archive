---
title: "E: postfix: subprocess installed post-installation script returned error exit status"
date: 2010-05-31
forum: General Help
---

### Post by Ichido on 2010-05-31
When I try to install software using Synaptic Package Manager, I receiving the following:
"E: postfix: subprocess installed post-installation script returned error exit status 75"

Can someone explain?

NEW Info:

dave@dave-laptop10:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libboost-regex1.40.0 libqt4-assistant libpackagekit-glib2-12
  libkscreensaver5 libsolidcontrolifaces4 linux-headers-2.6.32-21
  libwxgtk2.8-0 plasma-widgets-workspace mysql-client-core-5.1
  libplasma-geolocation-interface4 kdesudo libpackagekit-qt-12
  mysql-server-core-5.1 install-package libqt4-help libksgrd4 python-qt4
  libsdl-sound1.2 linux-headers-2.6.32-21-generic kdebase-workspace-bin
  python-sip libkworkspace4 libplasmagenericshell4 libkfontinst4
  libwxbase2.8-0 libsigc++-1.2-5c2 python-packagekit packagekit libkephal4
  gdebi-kde kdebase-workspace-data software-properties-kde ksysguardd
  libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins
  libsolidcontrol4 akonadi-server update-manager-kde packagekit-backend-apt
  libphysfs1 libplasma-applet-system-monitor4 libqt4-scripttools
  libprocesscore4 python-kde4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 04
[B]newaliases: fatal: file /etc/postfix/main.cf: parameter mydomain: bad parameter value: 04
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

---

