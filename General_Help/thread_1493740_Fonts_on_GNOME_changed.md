---
title: "Fonts on GNOME changed"
date: 2010-05-26
forum: General Help
---

### Post by Blue Omega on 2010-05-26
Hello,

Yesterday I've installed KDE (kubuntu-desktop) upon Ubuntu to give it a try after a very long time I didn't use KDE. I decided to remove it and go back to GNOME.
I removed the KDE packages using this sudo:
```
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint freespacenotifier gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 icoutils ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kbluetooth kcalc kcm-gtk kcm-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knm-runtime knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete kopete-message-indicator korganizer kpackagekit kppp krdc krfb krosspython ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libattica0 libaudio2 libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libepub0 libexiv2-6 libflac++6 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkcddb4 libkdcraw8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-8 libkfontinst4 libkipi7 libkleo4 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libkwineffects1 libkworkspace4 liblastfm0 libmimelib4 libmng1 libmodplug0c2 libmpcdec3 libmsn0.3 libmysqlclient16 libokularcore1 libotr2 libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3 libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3 libprocesscore4 libprocessui4 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libsolidcontrol4 libsolidcontrolifaces4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libtag-extras1 libtaskmanager4 libvncserver0 libweather-ion4 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-client-core-5.1 mysql-common mysql-server-core-5.1 network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme oxygen-icon-theme oxygen-icon-theme-complete packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-scriptengine-javascript plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback plasma-widget-message-indicator plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo polkit-kde-1 printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip quassel quassel-data shared-desktop-ontologies software-properties-kde soprano-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde usb-creator-kde userconfig virtuoso-nepomuk && sudo apt-get install ubuntu-desktop
```
The KDE has been removed but some how some of the font changed.

[IMG]http://bayimg.com/image/aandcaaca.jpg[/IMG]

The font settings in the Appearance->Fonts are as they suppose to be (Sans,10...).

How can I correct that?

Using Ubuntu 10.04.

---

### Post by bohoomil on 2010-06-06
Have you tried removing KDE desktop this way?

```
http://www.psychocats.net/ubuntu/puregnome
```

---

### Post by Blue Omega on 2010-06-06
> **bohoomil said:**
> Have you tried removing KDE desktop this way?

```
http://www.psychocats.net/ubuntu/puregnome
```

That's the same code I've posted, I took it from that site.

---

### Post by bohoomil on 2010-06-06
I'm sorry, I didn't realize that.

I've recently done exactly the same (installed KDE SC next to Gnome) and had the same issue with fonts. You can try doing what I did (unfortunately, the access to KDE's System Settings panel is required): open KDE System Settings, select "Appearance" and then "Fonts" and there you have to change settings so they match your Gnome ones (including anti-aliasing). The fonts should look OK then.

---

