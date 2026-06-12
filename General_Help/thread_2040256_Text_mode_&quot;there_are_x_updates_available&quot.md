---
title: "Text mode &quot;there are x updates available&quot; notification tool?"
date: 2012-08-10
forum: General Help
---

### Post by codell on 2012-08-10
In text mode I'd like to see "there are x updates available".

How I wish it to work:
- run apt-get update in background
- notify me about the result "there are x updates available"

Or can I run a tool, which tells me in text mode?

$ update-notifier
There are 50 updates available.

Is there such a tool?

---

### Post by nothingspecial on 2012-08-10
byobu will tell you that if you check the "updates-available" box in the status notifications menu.

[ATTACH]222513[/ATTACH]

---

### Post by cortman on 2012-08-10
The standard Update Manager for Ubuntu will tell you how many updates are available, and how large the download will be. So will the command

```
sudo apt-get upgrade
```

AFAIK.

---

### Post by Vaphell on 2012-08-10
apt-get with -s should run in simulation mode, so you can do a dry run of *apt-get upgrade* and find the line where the packages are counted.
```
$ apt-get -s upgrade | grep '^[0-9]'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

if you want to format the message, you can pass it to sed or whatever

```
$ apt-get -s upgrade | grep '^[0-9]' | sed -r 's/([0-9]+)[^0-9]+([0-9]+)[^0-9]+([0-9]+)[^0-9]+([0-9]+)[^0-9]+/to upgrade: \1\nto install: \2\nto remove: \3\nto ignore: \4/'
to upgrade: 0
to install: 0
to remove: 0
to ignore: 0
```

---

### Post by codell on 2012-08-10
How does the notification work on Ubuntu Server? "there are x updates available" I've seen it but I never knew which package it was.

---

### Post by cortman on 2012-08-10
Just run

```
sudo apt-get upgrade
```


??? On my (admittedly quite outdated) VBox:

```
cortman@cortman-VirtualBox:~$ sudo apt-get upgrade
[sudo] password for cortman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  hplip hplip-data libhpmud0 libsane-hpaio linux-generic linux-headers-generic
  linux-image-generic printer-driver-hpcups printer-driver-hpijs
The following packages will be upgraded:
  accountsservice akregator apparmor apport apport-gtk apport-kde apt
  apt-transport-https apt-utils aptdaemon aptdaemon-data ark at-spi2-core
  bamfdaemon bind9-host compiz compiz-core compiz-gnome compiz-plugins-default
  cron cups cups-bsd cups-client cups-common cups-filters cups-ppdc
  desktop-file-utils dnsutils dolphin dragonplayer empathy empathy-common eog
  evince evince-common firefox-locale-en fonts-liberation fonts-opensymbol
  foomatic-filters freespacenotifier ghostscript ghostscript-cups
  ghostscript-x gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gst-plugins-base-0.10 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-pango-1.0 gir1.2-rb-3.0 gir1.2-ubuntuoneui-3.0 gir1.2-unity-5.0
  gir1.2-webkit-3.0 gnome-accessibility-themes gnome-control-center
  gnome-control-center-data gnome-desktop3-data gnome-games-data
  gnome-icon-theme gnome-media gnome-orca gnome-settings-daemon gnome-sudoku
  gnomine grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-alsa
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-x
  gwenview gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter initscripts isc-dhcp-client
  isc-dhcp-common kaddressbook kamera kate kate-data katepart kcalc
  kde-baseapps-bin kde-baseapps-data kde-runtime kde-runtime-data
  kde-style-oxygen kde-wallpapers-default kde-window-manager
  kde-window-manager-common kde-workspace kde-workspace-bin kde-workspace-data
  kde-workspace-kgreet-plugins kde-zeroconf kdegames-card-data
  kdegraphics-strigi-analyzer kdelibs-bin kdelibs5-data kdelibs5-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-kresources
  kdepim-runtime kdepim-strigi-plugins kdepimlibs-kio-plugins kdm kdoctools
  khelpcenter4 kinfocenter klipper kmail kmenuedit kmix knotes konsole kontact
  kopete korganizer kpat kppp krb5-locales ksysguard ksysguardd ksystemlog
  kubuntu-docs kwalletmanager landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  libaccountsservice0 libakonadi-calendar4 libakonadi-contact4
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4
  libakonadi-notes4 libapt-inst1.4 libapt-pkg4.12 libasound2 libatspi2.0-0
  libbamf0 libbamf3-0 libbind9-80 libcairo-gobject2 libcairo2
  libcalendarsupport4 libcups2 libcupscgi1 libcupsdriver1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdecoration0 libdns81 libeventviews4 libevince3-3
  libexif12 libexpat1 libfreerdp-plugins-standard libfreerdp1 libgail-3-0
  libgcrypt11 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-0
  libglib2.0-bin libglib2.0-data libglu1-mesa libgnome-control-center1
  libgnome-desktop-3-2 libgnutls26 libgpgme++2 libgphoto2-2 libgphoto2-l10n
  libgphoto2-port0 libgrip0 libgs9 libgs9-common libgssapi-krb5-2
  libgstreamer-plugins-base0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgtksourceview-3.0-0 libgtksourceview-3.0-common libgudev-1.0-0
  libgutenprint2 libgwibber-gtk2 libgwibber2 libincidenceeditorsng4 libisc83
  libisccc80 libisccfg82 libjavascriptcoregtk-3.0-0 libjpeg-turbo8
  libk5crypto3 libkabc4 libkactivities-bin libkactivities6 libkalarmcal2
  libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4
  libkcalutils4 libkcddb4 libkcmutils4 libkde3support4 libkdeclarative5
  libkdecorations4 libkdecore5 libkdegames5a libkdepim4
  libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2
  libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10 libkexiv2-data
  libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5
  libkipi-data libkipi8 libkjsapi4 libkjsembed4 libkldap4 libkleo4
  libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common
  libkonq5-templates libkonq5abi1 libkontactinterface4 libkopete4 libkparts4
  libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4
  libkpty4 libkrb5-3 libkrb5support0 libkresources4 libkrosscore4
  libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4
  libktexteditor4 libktnef4 libkunitconversion4 libkwineffects1abi3
  libkwinglutils1 libkwinnvidiahack4 libkworkspace4abi1 libkxmlrpcclient4
  libldap-2.4-2 liblightdm-gobject-1-0 liblwres80 libmailcommon4
  libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4
  libmessageviewer4 libmicroblog4 libmtp-common libmtp-runtime libmtp9
  libmysqlclient18 libnautilus-extension1a libnepomuk4
  libnepomukdatamanagement4 libnepomukquery4a libnepomuksync4 libnepomukutils4
  libnm-glib-vpn1 libnm-glib4 libnm-util2 libokularcore1abi1 libpango1.0-0
  libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi3
  libplasmagenericshell4 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libprocesscore4abi1 libprocessui4a
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libpython2.7 libqgpgme1 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-kde libreoffice-math
  libreoffice-style-human libreoffice-style-oxygen libreoffice-style-tango
  libreoffice-writer librhythmbox-core5 libsmbclient libsnmp-base libsnmp15
  libsolid4 libsolidcontrol4abi2 libsolidcontrolifaces4abi2 libssl1.0.0
  libsyncdaemon-1.0-1 libsyndication4 libtaskmanager4abi3 libtemplateparser4
  libthreadweaver4 libtiff4 libubuntuoneui-3.0-1 libudev0 libunity-2d-private0
  libunity-core-5.0-5 libunity9 libutouch-geis1 libv4l-0 libv4lconvert0
  libwbclient0 libweather-ion6 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libxatracker1 libxkbfile1 libxslt1.1 lightdm linux-headers-3.2.0-24
  linux-headers-3.2.0-24-generic linux-image-3.2.0-24-generic linux-libc-dev
  mahjongg mysql-client-core-5.5 mysql-common mysql-server-core-5.5 nautilus
  nautilus-data nautilus-sendto-empathy network-manager ntpdate okular
  okular-extra-backends oneconf openssl oxygen-icon-theme
  plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop
  plasma-netbook plasma-scriptengine-javascript plasma-scriptengine-python
  plasma-widget-folderview plasma-widget-kimpanel plasma-widgets-addons
  plasma-widgets-workspace policykit-1 printer-driver-gutenprint
  printer-driver-ptouch psmisc pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-crypto python-cupshelpers python-debtagshw python-gi python-gi-cairo
  python-gobject python-kde4 python-piston-mini-client python-problem-report
  python-software-properties python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python2.7 python2.7-minimal qdbus remmina remmina-common remmina-plugin-rdp
  remmina-plugin-vnc resolvconf rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common samba-common-bin
  shared-mime-info shotwell smbclient software-center
  software-properties-common software-properties-gtk software-properties-kde
  ssl-cert sudo system-config-printer-common system-config-printer-gnome
  system-config-printer-kde system-config-printer-udev systemsettings sysv-rc
  sysvinit-utils tasks-icons telepathy-gabble thunderbird
  thunderbird-globalmenu thunderbird-gnome-support ubuntu-docs
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel udev udisks unity unity-2d
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-common
  unity-greeter unity-lens-music unity-lens-video unity-scope-musicstores
  unity-scope-video-remote unity-services uno-libs3 update-manager
  update-manager-core update-manager-kde update-notifier
  update-notifier-common ure vino xdiagnose xkb-data xserver-common
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-vmmouse
  xserver-xorg-video-vmware xsettings-kde xul-ext-ubufox
[B]528 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 415 MB of archives.
After this operation, 4,906 kB of additional disk space will be used.[/B]
Do you want to continue [Y/n]? 

```

This looks pretty clear to me.
Vaphell FTW- that is some scripting genius.

---

### Post by codell on 2012-08-11
Actually I was looking for

/usr/lib/update-notifier/apt-check --human-readable

---

### Post by rov4416444 on 2012-08-11
For the server-based utility do:

apt-get install update-notifier-common


Just a fair warning that it is somewhat flaky, I assume by design so that logins don't get wedged. If it doesn't seem to update for a long time or stops showing up at all, rm -rf /var/lib/update-notifier/* and relogin. The lack of those files will induce it to regenerate them (or try to, at least).

Also, this shows up with the motd, so if you disable that in any way (.hushlogin file, messing with sshd or pam settings, etc.) it'll not work right.

---

