---
title: "Remove kde desktop environment"
date: 2011-01-05
forum: General Help
---

### Post by Bucky Ball on 2011-01-05
Hi all,

Just a quicky. My desktop is a bit of a hybrid: Xubuntu installed first then added UStudio AV packages, kde DE, Gnome DE, openbox and a few other things. Works for me! Up an running in 8.04 like this for a couple of years. Just upgraded from 8.04 to 10.04 LTS (there are a  few threads to post about the issues that's left me with!!!) and I just  noticed in the updates there is a whole bunch of updates for kde because  the packages I have are probably left over from 8.04 and out of date. 

My question: How do I delete the kde DE simply, without going through Synpatics and removing every kde related package?? I don't want 'em. Just want to get rid of  kde DE and all related stuff  so the kde updates don't appear in Update Manager, then update.

Reason: I don't ever use kde. Don't dig it. 

To be honest, I used it so little I forgot I even had kde DE on here! 

Thanks in advance ... :)

---

### Post by James_Lochhead on 2011-01-05
What I would do is:

1) Load a 10.04 Live CD. 
2) Open a terminal.
3) Type:
 
sudo apt-get install kubuntu-desktop

4) Wait for the packages to get listed.
5) Rather than accept the install type n.
6) Copy the list of packages in to a text file and save on a memory stick (or on a partition somewhere).

7) Load up normally without the Live CD and type sudo apt-get remove <package list from text file>

Some formatting might be necessary.

**Make sure you read through the package list and delete anything you actually use.**

---

### Post by James_Lochhead on 2011-01-05
Mine looks like:

akonadi-server akregator amarok amarok-common amarok-utils apport-kde
  apturl-kde ark bluedevil bluez bluez-alsa bluez-cups cdparanoia cdrdao
  docbook-xsl docbook-xsl-doc-html dolphin dragonplayer gdebi-core gdebi-kde
  gnupg-agent gnupg2 gtk2-engines-qtcurve gwenview hal hal-info ibus-qt4
  jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk
  kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data
  kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins
  kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5
  kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd
  kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind
  khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime
  knotes konsole kontact kopete kopete-message-indicator korganizer
  kpackagekit kppp krosspython ksnapshot ksysguard ksysguardd ksystemlog
  ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-firefox-installer
  kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings
  kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt
  libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprivate1 libao-common libao4 libattica0
  libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl
  libdbusmenu-qt2 libdebconf-kde0 libepub0 libflac++6 libgpgme++2 libgps19
  libhal-storage1 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkabc4
  libkatepartinterfaces4 libkblog4 libkcal4 libkcddb4 libkdcraw8
  libkde3support4 libkdecorations4 libkdecore5 libkdepim4 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkephal4 libkexiv2-8 libkfile4 libkholidays4
  libkhtml5 libkimap4 libkimproxy4 libkio5 libkipi7 libkjsapi4 libkjsembed4
  libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5 libkonq5-templates
  libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4
  libkpimtextedit4 libkpimutils4 libkpty4 libkresources4 libkrosscore4
  libkrossui4 libksba8 libkscreensaver5 libksgrd4 libksieve4
  libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2
  libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4
  libkxmlrpcclient4 liblastfm0 libloudmouth1-0 libmailtransport4
  libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmsn0.3
  libnepomuk4 libnepomukquery4a libokularcore1 libotr2 libpackagekit-glib2-14
  libpackagekit-qt-14 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3
  libprocesscore4a libprocessui4a libqalculate5 libqapt-runtime libqapt1
  libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql
  libqtscript4-uitools libqtscript4-xml libreadline5 libsolid4
  libsolidcontrol4a libsolidcontrolifaces4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1
  libtaskmanager4a libthreadweaver4 libvirtodbc0 libweather-ion4a libzip1
  mysql-client-core-5.1 mysql-server-core-5.1 network-manager-pptp-kde okular
  okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen
  oxygen-cursor-theme oxygen-icon-theme packagekit packagekit-backend-aptcc
  pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons
  plasma-dataengines-workspace plasma-desktop plasma-netbook
  plasma-scriptengine-javascript plasma-scriptengine-python
  plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel
  plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback
  plasma-widget-menubar plasma-widget-message-indicator
  plasma-widget-networkmanagement plasma-widget-quickaccess
  plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo
  plymouth-theme-kubuntu-text polkit-kde-1 printer-applet python-kde4
  python-packagekit python-qt4 python-qt4-dbus python-sip qapt-batch quassel
  quassel-data rekonq shared-desktop-ontologies smartdimmer
  software-properties-kde soprano-daemon system-config-printer-kde
  systemsettings update-manager-kde usb-creator-kde userconfig
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common

**But I'm running 10.10 so there are probably some differences.**

---

### Post by HermanAB on 2011-01-05
Hmm, you cannot unscramble a dozen eggs.  Trying to remove a desktop environment is bound to end in tears.

Just install whatever other DE you want and select it at boot time.  Many other distributions ship with multiple DEs.  I frequently toggle between Gnome/KDE/LXDE depending on what I feel like in the morning.

---

### Post by aysiu on 2011-01-05
> **James_Lochhead said:**
> What I would do is:

1) Load a 10.04 Live CD. 
2) Open a terminal.
3) Type:
 
sudo apt-get install kubuntu-desktop

4) Wait for the packages to get listed.
5) Rather than accept the install type n.
6) Copy the list of packages in to a text file and save on a memory stick (or on a partition somewhere).

7) Load up normally without the Live CD and type sudo apt-get remove <package list from text file>

Some formatting might be necessary.

**Make sure you read through the package list and delete anything you actually use.** I already did this for you. No need to do it again.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Bucky Ball on 2011-01-06
> **HermanAB said:**
> Hmm, you cannot unscramble a dozen eggs.  Trying to remove a desktop environment is bound to end in tears.

Just install whatever other DE you want and select it at boot time.  Many other distributions ship with multiple DEs.  I frequently toggle between Gnome/KDE/LXDE depending on what I feel like in the morning.

I removed KDE DE yesterday on my laptop and it was easy. Just took awhile. I just wanted to know if there was a quicker way of doing it. I already have quite a few other DEs installed, thanks Herman, as mentioned post #1. Re-read. ;)

> **aysiu said:**
> I already did this for you. No need to do it again.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Cheers, aysiu.

---

### Post by Bucky Ball on 2011-01-06
> **James_Lochhead said:**
> Mine looks like:

akonadi-server akregator amarok amarok-common amarok-utils apport-kde
  apturl-kde ark bluedevil bluez bluez-alsa bluez-cups cdparanoia cdrdao
  docbook-xsl docbook-xsl-doc-html dolphin dragonplayer gdebi-core gdebi-kde
  gnupg-agent gnupg2 gtk2-engines-qtcurve gwenview hal hal-info ibus-qt4
  jockey-kde k3b k3b-data kaddressbook kamera kate kcalc kde-config-gtk
  kde-config-touchpad kde-window-manager kde-zeroconf kdebase-bin kdebase-data
  kdebase-runtime kdebase-runtime-data kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-kgreet-plugins
  kdegraphics-libs-data kdegraphics-strigi-plugins kdelibs-bin kdelibs5
  kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd
  kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins
  kdepim-wizards kdepimlibs-kio-plugins kdesudo kdm kdoctools kfind
  khelpcenter4 kinfocenter klipper kmag kmail kmix kmousetool knm-runtime
  knotes konsole kontact kopete kopete-message-indicator korganizer
  kpackagekit kppp krosspython ksnapshot ksysguard ksysguardd ksystemlog
  ktorrent ktorrent-data kubuntu-debug-installer kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-firefox-installer
  kubuntu-konqueror-shortcuts kubuntu-netbook-default-settings
  kubuntu-notification-helper kvkbd kwalletmanager language-selector-qt
  libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprivate1 libao-common libao4 libattica0
  libbluedevil1 libboost-program-options1.42.0 libcln6 libclucene0ldbl
  libdbusmenu-qt2 libdebconf-kde0 libepub0 libflac++6 libgpgme++2 libgps19
  libhal-storage1 libibus-qt1 libindicate-qt0 libiodbc2 libk3b6 libkabc4
  libkatepartinterfaces4 libkblog4 libkcal4 libkcddb4 libkdcraw8
  libkde3support4 libkdecorations4 libkdecore5 libkdepim4 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkephal4 libkexiv2-8 libkfile4 libkholidays4
  libkhtml5 libkimap4 libkimproxy4 libkio5 libkipi7 libkjsapi4 libkjsembed4
  libkldap4 libkleo4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq5 libkonq5-templates
  libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4
  libkpimtextedit4 libkpimutils4 libkpty4 libkresources4 libkrosscore4
  libkrossui4 libksba8 libkscreensaver5 libksgrd4 libksieve4
  libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libktorrent2
  libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4
  libkxmlrpcclient4 liblastfm0 libloudmouth1-0 libmailtransport4
  libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libmsn0.3
  libnepomuk4 libnepomukquery4a libokularcore1 libotr2 libpackagekit-glib2-14
  libpackagekit-qt-14 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4b libplasmagenericshell4 libpolkit-qt-1-0 libpoppler-qt4-3
  libprocesscore4a libprocessui4a libqalculate5 libqapt-runtime libqapt1
  libqca2 libqca2-plugin-ossl libqgpgme1 libqimageblitz4 libqjson0
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql
  libqtscript4-uitools libqtscript4-xml libreadline5 libsolid4
  libsolidcontrol4a libsolidcontrolifaces4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libsyndication4 libtag-extras1
  libtaskmanager4a libthreadweaver4 libvirtodbc0 libweather-ion4a libzip1
  mysql-client-core-5.1 mysql-server-core-5.1 network-manager-pptp-kde okular
  okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen
  oxygen-cursor-theme oxygen-icon-theme packagekit packagekit-backend-aptcc
  pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons
  plasma-dataengines-workspace plasma-desktop plasma-netbook
  plasma-scriptengine-javascript plasma-scriptengine-python
  plasma-widget-facebook plasma-widget-folderview plasma-widget-kimpanel
  plasma-widget-kimpanel-backend-ibus plasma-widget-kubuntu-feedback
  plasma-widget-menubar plasma-widget-message-indicator
  plasma-widget-networkmanagement plasma-widget-quickaccess
  plasma-widgets-addons plasma-widgets-workspace plymouth-theme-kubuntu-logo
  plymouth-theme-kubuntu-text polkit-kde-1 printer-applet python-kde4
  python-packagekit python-qt4 python-qt4-dbus python-sip qapt-batch quassel
  quassel-data rekonq shared-desktop-ontologies smartdimmer
  software-properties-kde soprano-daemon system-config-printer-kde
  systemsettings update-manager-kde usb-creator-kde userconfig
  virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common

**But I'm running 10.10 so there are probably some differences.**

Cheers. I tried this yesterday when removing KDE DE from my laptop. Just gave me a whole bunch of errors and didn't remove anything. :(

---

