---
title: "New release update in update manager"
date: 2009-12-08
forum: General Help
---

### Post by ubudog on 2009-12-08
Hi, I have kubuntu 9.04 on my desktop and I want to upgrade it to Ubuntu 9.10.  Can I set it to upgrade from kubuntu to ubuntu in update manager?

---

### Post by whoop on 2009-12-08
> **ubudog said:**
> Hi, I have kubuntu 9.04 on my desktop and I want to upgrade it to Ubuntu 9.10.  Can I set it to upgrade from kubuntu to ubuntu in update manager?

No, you cannot do this directly... Not to worry, best approach (imo) would be to:

1: run this command (to switch from kubuntu to ubuntu) :
```

sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop

```
source:[http://www.psychocats.net/ubuntu/puregnomejaunty](http://www.psychocats.net/ubuntu/puregnomejaunty)

2:
upgrade to 9.10 using update manager...

---

### Post by ubudog on 2009-12-08
Also, could I just install ubuntu-desktop?

---

### Post by ubudog on 2009-12-08
And then after that, go into ubuntu and remove kubuntu-desktop?

---

### Post by whoop on 2009-12-08
> **ubudog said:**
> Also, could I just install ubuntu-desktop?

Yeah, sure:
```

sudo apt-get update && sudo apt-get install ubuntu-desktop

```
source:[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

---

### Post by whoop on 2009-12-08
> **ubudog said:**
> And then after that, go into ubuntu and remove kubuntu-desktop?

Yeah, run the command I suggested earlier for that:
```

sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig && sudo apt-get install ubuntu-desktop

```


the sub-command
```

 && sudo apt-get install ubuntu-desktop

```
probably isn't necessary, but it won't hurt. It's safe...
Also, although I have never tried, I wouldn't remove kde while it is running (run the command while running Gnome or command line only)...

---

### Post by ubudog on 2009-12-08
OK, thanks for all your help!

---

### Post by wilee-nilee on 2009-12-08
Some have had problems with upgrading from 9.04 to 9.10 and this upgrade will not give you the new ext4 setup. So no matter what backup what you can't afford to lose.

The general advice with karmic is a fresh install that you can then add back what you needed to back up anyway.

The new ext4 is a snappier running setup, also with this fresh install is grub 2 so make sure you understand the ramifications of this new setup before you act, don't just upgrade thinking your completely safe to do so.

@whoop I can appreciate your trying to help this person but no mention of backing up at the least is a weak set of instructions.

Op I would carefully look through the forum and web before you act.

---

### Post by whoop on 2009-12-08
> **wilee-nilee said:**
> Some have had problems with upgrading from 9.04 to 9.10 and this upgrade will not give you the new ext4 setup. So no matter what backup what you can't afford to lose.

The general advice with karmic is a fresh install that you can then add back what you needed to back up anyway.

The new ext4 is a snappier running setup, also with this fresh install is grub 2 so make sure you understand the ramifications of this new setup before you act, don't just upgrade thinking your completely safe to do so.

@whoop I can appreciate your trying to help this person but no mention of backing up at the least is a weak set of instructions.

Op I would carefully look through the forum and web before you act.

The question in this thread was not really concerning the upgrade, it was concerning switching window managers, well at least I interpreted in that way. "My instructions" have nothing to do with the upgrade process itself. Although I do usually state "back up" when people have questions concerning an upgrade, I never really get people backing up in one situation and not backing up in another... I backup weekly, it doesn't really have to do anything with what I do.

I upgraded from 9.04 to 9.10 (as I never do fresh installs),
Converted my filesystem from ext3 to ext4 via: [http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)
Upgraded from grub1 to grub2 via: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by wilee-nilee on 2009-12-08
My main reason for responding was that the OP may want to upgrade. Since there are no statistics on the failure of this or the failure of upgrading the ext it seems that following a method with this release that is the safest and most straight forward seems like the best approach.

Your upgrade and and having to upgrade the extension must have at the least taken about 4 times the time a fresh install would have, and had many areas it could have failed.

---

### Post by whoop on 2009-12-08
> **wilee-nilee said:**
> My main reason for responding was that the OP may want to upgrade. Since there are no statistics on the failure of this or the failure of upgrading the ext it seems that following a method with this release that is the safest and most straight forward seems like the best approach.

Your upgrade and and having to upgrade the extension must have at the least taken about 4 times the time a fresh install would have, and had many areas it could have failed.

I maintain 25 ubuntu machines atm, with specific packages and custom software installed on them. Performing fresh installs, like so many (new) Ubuntu users seem to do these days would take a lot of time, Upgrading takes no time at all. Although I have had to make some manual changes along the years, it keeps me up to date of structural changes in the distributions I use.

For me fresh installs are slow, manual intensive and most important non-educational.

---

