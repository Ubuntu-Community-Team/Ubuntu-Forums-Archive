---
title: "My mouse pointer is stuck in Kubuntu mode, How to i switch it back to GNOME?"
date: 2010-06-09
forum: General Help
---

### Post by robot_chicken_parm on 2010-06-09
Hi.  I am using Ubuntu 10.04, and yesterday i decided to try out KDE for the first time.  I installed it from a link in the Ubuntu Help Center:  Located in the topic "Customizing Your Computer" in the topic Using KDE or Xfce instead of the GNOME desktop.  I tried it and didn't like it.  No offense to the developers or to anyone who does like it, it just wasnt for me.  And i AM eternally greatful for the wealth of quality software available to people, and for FREE no less!  Anyway, getting to the point...  I deleted it KDE,  "sudo apt-get remove KDEbase-bin" to be specific.  I found that here([http://ubuntuforums.org/showthread.php?t=1435757](http://ubuntuforums.org/showthread.php?t=1435757)).

My problem is that i am stuck with the mouse pointer from KDE in Gnome and i am unable to change it.  Any help would be appreciated.  I went to the mouse pointer in appearance preferences under the current theme and changed it to DMZ Black, which is the pointer i prefer, however that only effects the mouse when it's inside of the Firefox window.  Any ideas?

---

### Post by SlidingHorn on 2010-06-09
Here's a way to get back to a pure gnome setup from KDE:

```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install ubuntu-desktop
```

Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by robot_chicken_parm on 2010-06-09
hi.  i copied and pasted into the terminal the above code, and it was taking a while so i left it going, and a few hours later went back and my computer was frozen, while making that clicking sound computers make when they're working hard, so i waited another half hour but the text in the terminal hadn't changed at all so i restarted.  it seems that nothing from kde has been yet deleted.  should i run the command again?

---

