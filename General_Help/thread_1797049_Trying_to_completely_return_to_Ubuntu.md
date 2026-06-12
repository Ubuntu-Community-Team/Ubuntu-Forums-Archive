---
title: "Trying to completely return to Ubuntu"
date: 2011-07-04
forum: General Help
---

### Post by ianc1 on 2011-07-04
I tried out Kubuntu today on Ubuntu by installing kubuntu-desktop.  I decided that it was too slow on my machine and whilst nice a bit too flashy for me.  So I tried to remove it doing:

```
sudo apt-get purge kubuntu-desktop
```On rebooting the machine, my grub menu is now on a blue background rather than purple and on booting the machine has a Kubuntu logo before reaching gdm where I login in.  I also still have Kubuntu Plasma desktop as an option.

I found all KDE packages and removed them by

```
dpkg -l | grep kde > file.txt
sudo apt-get purge $(< file.txt)
sudo update-grub
```I still have a blue grub screen, Kubuntu logo on boot etc.  Why ????? How do I fix this and return to Ubuntu and only Ubuntu with Unity.

I am aware of Psychocats post about returning to pure Gnome, [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome), but this gives dependency errors.

Thanks in advance.

---

### Post by wojox on 2011-07-04
Remove plymouth-theme-kubuntu-logo and plymouth-theme-kubuntu-text.

---

### Post by ianc1 on 2011-07-04
Thanks got rid of those.

I also looked into /var/log/apt/history.log to see what was actually installed and purged those packages.  In case any one else stumbles on this post the packages installed can be removed with

```
sudo apt-get purge kpat libkcmutils4 qapt-batch libclucene0ldbl ksystemlog plasma-dataengines-workspace krdc krfb plasma-netbook libkldap4 kppp kubuntu-debug-installer libktnef4 userconfig kubuntu-default-settings kdepim-runtime libqca2 libqimageblitz4 python-pyudev kdebase-workspace libdebconf-kde0 knm-runtime polkit-kde-1 libtaskmanager4b kdegames-card-data libbluedevil1 libpackagekit-glib2-14 libkpimtextedit4 pinentry-gtk2 rekonq libkscreensaver5 libkcalutils4 libkimproxy4 libk3b6 plasma-widget-quickaccess libmicroblog4 kpackagekit plymouth-theme-kubuntu-logo freespacenotifier printer-applet ksnapshot libkipi8 nepomukcontroller libkjsembed4 libotr2 kdepim-groupware oxygen-icon-theme kdebase-runtime libkleo4 quassel-data libboost-program-options1.42.0 plasma-widgets-workspace kdebase-data gwenview libkemoticons4 libkdecore5 okular-extra-backends libmessagelist4 mysql-client-core-5.1 language-selector-kde libkidletime4 libkdegames5 quassel libqt4-qt3support libkxmlrpcclient4 docbook-xsl kcalc plasma-dataengines-addons libktorrent2 libgps19 shared-desktop-ontologies libvncserver0 klipper amarok-common libmimelib4 kdemultimedia-kio-plugins gtk2-engines-oxygen kontact gdebi-core ibus-qt4 kde-config-gtk ksysguard libkexiv2-9 libplasma-geolocation-interface4 libpowerdevilcore0 odbcinst libkcddb4 libntrack-qt4-1 libcln6 kopete-message-indicator apturl-kde plasma-widget-kimpanel-backend-ibus libkatepartinterfaces4 libprocesscore4b kubuntu-desktop dolphin libreoffice-style-oxygen libsolid4 kdesudo virtuoso-minimal k3b-data libloudmouth1-0 kde-zeroconf cryptsetup libkde3support4 kubuntu-konqueror-shortcuts libnepomuk4 libprocessui4a konsole libkdewebkit5 libqjson0 libktorrent-l10n korganizer k3b libsoprano4 mysql-server-core-5.1 plasma-widget-menubar libpolkit-qt-1-1 akregator libkcalcore4 libqtscript4-core libkdnssd4 libksgrd4 plasma-widget-networkmanagement libkparts4 kamera ark libkpgp4 libqgpgme1 libplasmaclock4b libpackagekit-qt14 plasma-scriptengine-declarative libmailtransport4 libqapt1 libakonadi-kde4 libqalculate5 libkabc4 libibus-qt1 kdebase-workspace-bin kvkbd libkworkspace4 kdelibs5-data libkresources4 libkdepim4 kdoctools libkdecorations4 libvirtodbc0 libkwineffects1a libkpimutils4 odbcinst1debian2 plymouth-theme-kubuntu-text kde-config-touchpad python-qt4-dbus libkprintutils4 krosspython libksieve4 libplasmagenericshell4 kfind kdebase-bin plasma-widget-facebook systemsettings usb-creator-kde kdm libksba8 kdegraphics-libs-data libkpimidentities4 icoutils amarok libkephal4a gnupg-agent libqtscript4-gui libqt4-sql-sqlite libkonq5a libqtscript4-uitools libthreadweaver4 libnepomukutils4 libkmediaplayer4 libkcal4 kdenetwork-filesharing kubuntu-docs knotes libsolidcontrol4a libntrack0 libknewstuff2-4 plasma-widget-message-indicator libkfile4 libkopete4 libknewstuff3-4 libqapt-runtime plasma-widget-kimpanel packagekit-backend-aptcc libkpty4 libindicate-qt1 kubuntu-netbook-default-settings kubuntu-firefox-installer libkblog4 python-packagekit network-manager-pptp-kde libkimap4 libpoppler-qt4-3 libstreamanalyzer0 kaddressbook libzip1 libknotifyconfig4 libasyncns0 packagekit libkntlm4 plasma-widgets-addons kinfocenter gdebi-kde libplasma3 libsolidcontrolifaces4a kdebase-workspace-data libqtscript4-sql software-properties-kde ksysguardd libkmime4 libweather-ion6 kdebase-workspace-kgreet-plugins kdelibs-bin partitionmanager libktexteditor4 libqtscript4-xml libattica0 libakonadi-contact4 khelpcenter4 libakonadi-kabc4 libkonq5-templates plasma-desktop libkholidays4 kdegraphics-strigi-plugins ktorrent-data libkio5 ktorrent jockey-kde akonadi-server libkjsapi4 bluedevil update-manager-kde libksignalplotter4 libstreams0 kwalletmanager libqca2-plugin-ossl libepub0 ktimetracker kdepim-strigi-plugins kopete plasma-widget-folderview libokularcore1 libtag-extras1 libkunitconversion4 kate kmail liblastfm0 virtuoso-opensource-6.1-common libmessagecore4 plasma-scriptengine-javascript kubuntu-notification-helper libssh-4 plasma-scriptengine-python libakonadiprotocolinternals1 soprano-daemon libakonadi-kcal4 amarok-utils libsyndication4 kdebase-runtime-data kde-window-manager apport-kde libreadline5 libiodbc2 libkhtml5 system-config-printer-kde libkdeui5 libakonadi-kmime4 dragonplayer libkdesu5 libqtscript4-network kdelibs5-plugins gpgsm kdepimlibs-kio-plugins gnupg2 okular kmousetool pinentry-qt4 libmsn0.3 virtuoso-opensource-6.1-bin kmag libkutils4 libkdcraw9 ntrack-module-libnl-0 kdepim-kresources libreoffice-kde kdepim-wizards libkrosscore4 libnepomukquery4a python-kde4 oxygen-icon-theme-complete libgpgme++2 kdepasswd kmix oxygen-cursor-theme libdmtx0a libmusicbrainz3-6 libkontactinterface4
```My Grub and splash screens have now returned to normal.

Once confusion remains though I thought apt-get purge removed settings files etc, yet in ~ I still have a .kde directory which is not empty and a .local/share/akonadi, again not empty.

Can I simply delete these which have ca 200 MB of contents?  And how can I locate any others for removal.  I know they are causing no harm, I simply want to remove them before I back up my system again.

Thanks

---

### Post by 3Miro on 2011-07-04
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

They have good tutorials about different DE.

---

### Post by wojox on 2011-07-05
This should work:

```
sudo rm /etc/alternatives/default.plymouth
sudo ln -s /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth /etc/alternatives/default.plymouth
```

---

### Post by ianc1 on 2011-07-05
Thanks 3Miro & wojox.

I'd already tried [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) which gave dependency issues.  I used the apt log in the end to remove all the packages.

So my system is back with Unity only and the appropriate Grub and Spash screens.

My remaining confusion is with the hidden directories that KDE puts in ~, eg .kde and .local/share/akonadi etc.

I thought removing the packages using apt-get purge should have taken away the config files and therefore these directories.  I simply wish to do the necessary "housekeeping" to remove these unnecessary items.  I am wary however that maybe I shouldn't just delete them and do not know how to locate them all.

---

