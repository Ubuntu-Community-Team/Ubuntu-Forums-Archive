---
title: "Problem with file permissions - files backed up from ubuntu"
date: 2011-12-30
forum: General Help
---

### Post by funkywimble on 2011-12-30
Hi,

I recently upgraded from Ubuntu 10.10 to 11.10 and unfortunately it is very slow, buggy and I just can't get into either gnome 3 or unity so I have decided to remove ubuntu and move to xubuntu. Before I do that I have backed up all my files onto an external hard drive with a view to moving them back into my personal folder once xubuntu is installed. So far so good!

However, I am right now using xubuntu from the live cd and I am having trouble accessing my files from the external hard drive due to permissions. I have tried going back into ubuntu and amending the permissions but this doesn't seem to have made a difference, the files are still showing with big crosses against them and some folders I can't access at all.

I don't want to install xubuntu until I know I will be able to access my old files. Does anyone have any idea what is causing this?

If you need any more information from me then just let me know.

Many thanks

M

---

### Post by Paqman on 2011-12-30
In both Ubuntu and Xubuntu the first user account gets the UID 1000, and subsequent accounts get 1001, 1002, etc. So if you have more than one account on your system then you can get ownership problems unless you set up the accounts in exactly the same order. I couldn't tell you exactly what UID the user on the live systems gets, but unless it matches you'll have trouble.

Don't worry though, just go ahead and install. You can take ownership of any files you want with the following command:
```
sudo chown -R username:username /path/to/files
```

Incidentally, you don't need to reinstall just to switch from Gnome/Unity to XFCE. Just install the package [xubuntu-desktop]("apt:xubuntu-desktop") and if you're happy to remove Gnome run this command:
```
sudo apt-get remove adium-theme-ubuntu apg appmenu-gtk appmenu-gtk3 appmenu-qt at-spi2-core bamfdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab binfmt-support bluez-gstreamer branding-ubuntu brasero brasero-cdrkit brasero-common checkbox checkbox-gtk cli-common compiz compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default compizconfig-backend-gconf deja-dup duplicity dvd+rw-tools empathy empathy-common eog evolution-data-server evolution-data-server-common example-content gbrainy gedit gedit-common geoclue geoclue-ubuntu-geoip ginn gir1.2-atspi-2.0 gir1.2-gnomebluetooth-1.0 gir1.2-gtksource-3.0 gir1.2-indicate-0.6 gir1.2-peas-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-wnck-3.0 gnome-bluetooth gnome-control-center gnome-control-center-data gnome-desktop3-data gnome-disk-utility gnome-font-viewer gnome-icon-theme-symbolic gnome-media gnome-nettool gnome-online-accounts gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-user-share gnome-utils-common growisofs gstreamer0.10-gconf gvfs-backends gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hwdata ibus-gtk3 indicator-appmenu indicator-datetime indicator-power indicator-session intel-gpu-tools libappindicator0.1-cil libarchive1 libatk-adaptor libatspi2.0-0 libaudio2 libbamf0 libbamf3-0 libboost-serialization1.46.1 libbrasero-media3-1 libcamel-1.2-29 libcanberra-pulse libcdio-cdda0 libcdio-paranoia0 libcdio10 libcompizconfig0 libdbus-glib1.0-cil libdbus1.0-cil libdbusmenu-qt2 libdconf-dbus-1-0 libdconf-qt0 libdconf0 libdecoration0 libebackend-1.2-1 libebook1.2-12 libecal1.2-10 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver1.2-15 libedataserverui-3.0-1 libexempi3 libfolks-telepathy25 libfolks25 libgail-3-common libgail-common libgconf2.0-cil libgdata-common libgdata1.7-cil libgdata13 libgdiplus libgdu-gtk0 libgeoclue0 libgexiv2-0 libgif4 libgkeyfile1.0-cil libglew1.5 libglewmx1.5 libglib2.0-bin libglib2.0-cil libglib2.0-data libgmime-2.4-2 libgmime2.4-cil libgnome-control-center1 libgnome-desktop-3-2 libgnome-media-profiles-3.0-0 libgnome-menu2 libgnome2-common libgnomekbd-common libgnomekbd7 libgoa-1.0-0 libgpgme11 libgpod-common libgpod4 libgtk-sharp-beans-cil libgtk2.0-cil libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common libgtkspell3-0 libgudev1.0-cil libgweather-3-0 libgweather-common libgwibber-gtk2 libgwibber2 libhyphen0 libidl0 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis2 libmetacity-private0 libmhash2 libmission-control-plugins0 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-csharp4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-drawing4.0-cil libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil libmtp-common libmtp-runtime libmtp9 libmysqlclient16 libmythes-1.2-0 libneon27-gnutls libnotify0.4-cil libnux-1.0-0 libnux-1.0-common liboauth0 liborbit2 liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 libpeas-1.0-0 libpeas-common libprotobuf7 libprotoc7 libpth20 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4 libquvi0 libraptor2-0 librasqal3 librdf0 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-writer librest-0.7-0 librsync1 libsdl1.2debian libsdl1.2debian-pulseaudio libstlport4.6ldbl libsyncdaemon-1.0-1 libtaglib2.0-cil libtelepathy-farsight0 libtelepathy-logger2 libtextcat-data libtextcat0 libtotem-plparser17 libtotem0 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-3.0-0 libunity-2d-private0 libunity-core-4.0-4 libunity-misc4 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libyajl1 libzeitgeist-1.0-1 light-themes media-player-info metacity metacity-common mono-4.0-gac mono-gac mono-runtime mousetweaks mysql-common nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share notify-osd notify-osd-icons nux-tools obexd-client overlay-scrollbar plymouth-theme-ubuntu-logo protobuf-compiler pulseaudio-module-bluetooth pulseaudio-module-gconf python-brlapi python-configglue python-dateutil python-egenix-mxdatetime python-egenix-mxtools python-farsight python-indicate python-libproxy python-louis python-papyon python-protobuf python-pyatspi2 python-pyinotify python-speechd python-support python-telepathy python-twisted-names python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno python-wnck qdbus qt-at-spi seahorse shotwell sni-qt ssh-askpass-gnome telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-indicator telepathy-logger telepathy-mission-control-5 telepathy-salut thunderbird-gnome-support tomboy totem totem-common totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk ubuntuone-couch ubuntuone-installer unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool unity-common unity-lens-applications unity-lens-files unity-lens-music unity-scope-musicstores unity-services uno-libs3 ure vino whois wodim xdiagnose xfonts-mathml zeitgeist zeitgeist-datahub zeitgeist-extension-fts && sudo apt-get install xubuntu-desktop 
```

---

### Post by funkywimble on 2011-12-30
You're totally right, I can now access them no bother, thanks! I did try to install the xubuntu desktop on ubuntu but it didn't really work properly for me... not sure what I did wrong but I just decided to install xubuntu from the live cd and now working perfectly - no issues and I can access my files fine!

Thanks again! :D

---

