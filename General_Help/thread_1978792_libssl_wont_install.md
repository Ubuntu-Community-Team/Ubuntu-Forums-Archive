---
title: "libssl wont install"
date: 2012-05-12
forum: General Help
---

### Post by strongbadia on 2012-05-12
trying to upgrade my distribution...

tom@theatre:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5) but 1.0.1-4ubuntu3 is installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu3) but 1.0.1-4ubuntu5 is installed
E: Unmet dependencies. Try using -f.

tom@theatre:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be REMOVED
  libgstfarsight0.10-0 libtelepathy-farsight0 python-farsight python-papyon telepathy-butterfly
The following NEW packages will be installed
  landscape-client-ui-install libarchive12 libfarstream-0.1-0 libgexiv2-1 libgmime-2.6-0 libgoa-1.0-common libidl-common libnettle4 libqt4-designer libqt4-help libqt4-scripttools libqt4-sql-sqlite libqt4-test libqtassistantclient4
  libqtwebkit4 libtelepathy-farstream2 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-image-3.2.0-24-generic python-qt4 python-qt4-dbus rhythmbox-mozilla rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist syslinux-legacy
  ubuntu-sso-client-qt ubuntu-wallpapers-precise ubuntuone-control-panel-qt unity-2d-common
The following packages will be upgraded:
  at-spi2-core compiz compiz-core compiz-gnome compiz-plugins-default dmsetup empathy empathy-common evolution-data-server evolution-data-server-common flashplugin-installer fonts-opensymbol gdb gir1.2-atspi-2.0 gir1.2-rb-3.0
  glib-networking glib-networking-common glib-networking-services gnome-online-accounts gnome-orca gnome-settings-daemon gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hdparm libatspi2.0-0 libcamel-1.2-29
  libdecoration0 libdevmapper-event1.02.1 libdevmapper1.02.1 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libgoa-1.0-0 libidl0 liblvm2app2.2
  libnm-glib-vpn1 libnm-glib4 libnm-util2 liborbit2 libpackagekit-glib2-14 libpurple0 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-impress libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer librhythmbox-core5 libsmbclient libssl1.0.0:i386 libsyncdaemon-1.0-1 libtasn1-3
  libtotem-plparser17 libunity-2d-private0 libunity-core-5.0-5 libutouch-geis1 libwbclient0 linux-generic linux-headers-generic linux-image-generic nautilus-sendto-empathy network-manager openssl python-central
  python-software-properties python-ubuntuone-client python-ubuntuone-control-panel python-uno qdbus remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rhythmbox rhythmbox-data rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone samba samba-common samba-common-bin shotwell simple-scan smbclient software-center software-properties-common software-properties-gtk sudo thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us ubuntu-desktop ubuntu-wallpapers ubuntuone-client ubuntuone-control-panel ubuntuone-control-panel-common ubuntuone-control-panel-gtk unity unity-2d unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-lens-applications unity-lens-music unity-scope-musicstores unity-services uno-libs3 update-manager update-manager-core upstart ure usb-creator-common usb-creator-gtk
  xserver-xorg-input-synaptics xul-ext-ubufox zenity zenity-common
154 upgraded, 29 newly installed, 5 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/264 MB of archives.
After this operation, 283 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libssl1.0.0

tom@theatre:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be upgraded:
  libssl1.0.0:i386
1 upgraded, 0 newly installed, 0 to remove and 153 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,004 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libssl1.0.0
tom@theatre:~$

Can anyone help?

Cheers
Tom

---

### Post by strongbadia on 2012-05-13
bump

---

