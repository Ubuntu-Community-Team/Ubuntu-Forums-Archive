---
title: "Completely Remove KDE / Kubuntu"
date: 2010-03-05
forum: General Help
---

### Post by DedMoroz on 2010-03-05
Recently, I installed Kubuntu onto my system to try it out. It was fine for a while, but I missed my Ubuntu setup. When I started using Ubuntu again, I noticed some strange things going on. Apparently, Ubuntu and Kubuntu have different startup app lists and they were getting confused with each other. On startup, these lists were getting confused with each other and crashing my system or causing it to take several minutes to load up.

I have several other issues since installing KDE, so I want to completely remove it. I have followed the instructions here...

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Those instructions appeared to work, until I rebooted... INTO KUBUNTU!! Worse yet, I had to re-install ALL of my applications again.

There must be some lingering Kubuntu stuff on my system if I am still allowed to boot into it.

How do I go about completely removing it? I would do a fresh install of Ubuntu, but dont have the time as this is my work system. Thanks for any tips!

---

### Post by sandyd on 2010-03-05
go to synaptic. remove every package that begins with "libqt4". then remove every package that begins with "kdelibs". all kde applications require qt to work. if you remove qt, the dependencies of the kde application will not be satisfied, and as a result, all programs related to kde will be removed due to dependency issues.

---

### Post by maddg3241 on 2010-03-05
To Remove it i have this command worked for me every time for 
 
Kubuntu put this in the terminal
 
sudo apt-get remove akonadi-server akregator amarok amarok-common amarok-utils apport-kde apturl-kde ark cdrdao dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ibus-qt4 ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kcm-gtk kde-icons-oxygen kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-groupware kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdesudo kdm kfind khelpcenter4 kipi-plugins klipper kmag kmail kmix kmousetool knotes konq-plugins konq-plugins-l10n konqueror konqueror-nsplugins konqueror-plugin-searchbar konqueror-plugins konsole kontact kopete korganizer kpackagekit kppp krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-firefox-installer kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin-style-qtcurve language-selector-qt libakonadiprivate1 libao2 libaudio2 libboost-program-options1.38.0 libclucene0ldbl libepub0 libexiv2-5 libfftw3-3 libflac++6 libindicate-qt0 libjpeg-progs libk3b6 libkabcommon4 libkcddb4 libkdcraw7 libkdecorations4 libkdepim4 libkexiv2-7 libkipi6 libkleo4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkontactinterfaces4 libkopete4 libkorundum4-ruby1.8 libkpgp4 libksane0 libksieve4 libkwineffects1 liblancelot0 liblastfm0 liblzma0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libokularcore1 libotr2 libpackagekit-glib11 libpackagekit-qt11 libplasma3 libpolkit-dbus2 libpolkit-grant2 libpolkit-qt0 libpolkit2 libpoppler-qt4-3 libqca2 libqca2-plugin-ossl libqimageblitz4 libqscintilla2-5 libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-ruby1.8 libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-sql libqtscript4-uitools libqtscript4-xml libruby1.8 libscim8c2a libsmokekde4-2 libsmokeqt4-2 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtag-extras1 libtidy-0.99-0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-server-core-5.1 okular okular-extra-backends openoffice.org-kde openoffice.org-style-oxygen oxygen-cursor-theme packagekit packagekit-backend-apt phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-scriptengine-python plasma-widget-facebook plasma-widget-folderview plasma-widget-googlecalendar plasma-widget-indicatordisplay plasma-widget-kimpanel plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-networkmanagement plasma-widget-quickaccess plasma-widgets-addons plasma-widgets-workspace policykit printer-applet python-kde4 python-packagekit python-qt4 python-qt4-dbus python-sip4 quassel quassel-data ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch system-config-printer-kde systemsettings ttf-arphic-uming ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde usb-creator-kde userconfig && sudo apt-get install ubuntu-desktop
 
Xubuntu
 
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial catfish exaile exo-utils feh fortune-mod fortunes-min giblib1 gigolo gnome-app-install gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgoffice-0-8 libgoffice-0-8-common libgtkmathview0c2a libid3tag0 libimlib2 liblink-grammar4 libotr2 libots0 libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 librecode0 libscim8c2a libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad orage pidgin pidgin-data pidgin-libnotify pidgin-otr policykit policykit-gnome psutils python-cddb python-mmkeys python-mutagen ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-arphic-uming ttf-liberation usb-creator usplash-theme-xubuntu vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop

---

### Post by sgage on 2010-03-05
I just use synaptic to remove all files with "kde" in them. Then I use an orphan finder (Ubuntu Tweak has one, but you can set an orphan filter in synaptic) to root out all the leftovers. Works for me.

---

### Post by nosmokenofire on 2011-05-25
> **sandyd said:**
> go to synaptic. remove every package that begins with "libqt4". then remove every package that begins with "kdelibs".

Many thanks SandyD. I had this problem and the only thing that worked for me was this solution. I tried everything else in the terminal but nothing worked. 

Just one last thing remains: a blue grub screen and a Kubuntu splash screen, any idea how to get back to my old Ubuntu grub and boot screens?

Thanks for any help.

---

### Post by iclestu on 2011-05-25
apologies if I am unfairly hijacking a thread but is there anyway to do the reverse? get rid of the gnome bits I am left with after having switched to kubuntu by simply installing from synaptic?

Its no biggie really, but i do occasionally see 'gnomy' stuff creeping in (including a splashscreen) that it would be just neater without....

---

### Post by Zorael on 2011-05-30
> **iclestu said:**
> apologies if I am unfairly hijacking a thread but is there anyway to do the reverse? get rid of the gnome bits I am left with after having switched to kubuntu by simply installing from synaptic?
Hmm, you could try removing **libgnome2-0** and let your package manager remove everything that depends on that. But it will probably leave some stuff out that merely recommend that package.

To grab *everything* that depends on the GTK libraries (which none of KDE's stuff do, except perhaps **gtk2-engines-oxygen** and other GTK-KDE compatibility libraries), remove **libgtk2.0-0**. >:3

Make note of stuff it removes along with it that you want to keep, like Chromium, Gimp, pulseaudio-module-gconf (not sure how well Pulseaudio does without this one), LibreOffice, flashplugin-installer, etc. Then simply reinstall them afterwards.
```
$ sudo aptitude purge libgtk2.0-0 -P
$ sudo aptitude purge ~c
```

---

### Post by abhilash29 on 2011-08-24
:mad:Dude your command "$ sudo aptitude purge libgtk2.0-0 -P" removed my complete gnome desktop, finally making it unusable.
I'm re-installing my system now. :x

---

### Post by Zorael on 2011-08-25
> **abhilash29 said:**
> :mad:Dude your command "$ sudo aptitude purge libgtk2.0-0 -P" removed my complete gnome desktop, finally making it unusable.
I'm re-installing my system now. :x
Please re-read the question the command was targeted against.

> **iclestu said:**
> apologies if I am unfairly hijacking a thread but is there anyway to do the reverse? **get rid of the gnome bits I am left with after having switched to kubuntu** by simply installing from synaptic?

Its no biggie really, but i do occasionally see 'gnomy' stuff creeping in (including a splashscreen) that it would be just neater without....

---

