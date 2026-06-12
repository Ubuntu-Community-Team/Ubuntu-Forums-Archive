---
title: "Really minimal?"
date: 2012-04-12
forum: General Help
---

### Post by Fxy on 2012-04-12
Ok sooo I'm looking to create a really minimal & lightweight system.  I have a custom environment set up with openbox & the only apps used are, chrome, pidgin, terminal, marlin & docky.  Is there anyway I can remove all the apps that go unused ( even default ones! ) & maybe all other desktop environments :?  My goal is to have a really lightweight & minimal system that boots up straight to the desktop in next to no time...

...Your opinions & suggestions are all welcome 



Fxy...

---

### Post by Megaptera on 2012-04-12
Have you looked at this option ...
"If you have a low-spec'ed computer (64 to 128 MB of RAM, less than 1 GHz processor), you may have difficulty with a regular Ubuntu installation. You may, even if you have a higher-spec'ed computer want to create a minimal installation for other reasons. "
Here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Hope it's of interest?

---

### Post by Fxy on 2012-04-12
> **Megaptera said:**
> Have you looked at this option ...
"If you have a low-spec'ed computer (64 to 128 MB of RAM, less than 1 GHz processor), you may have difficulty with a regular Ubuntu installation. You may, even if you have a higher-spec'ed computer want to create a minimal installation for other reasons. "
Here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Hope it's of interest?

I already have the full spec version of Ubuntu running the computer.  I'm just looking to create a minimal desktop using openbox, that's all...  ...All I would like to know is there anyway I can remove/delete all the applications & desktop environments I currently don't use :?  The apps listed in my original post are the only apps I use.



Fxy...

---

### Post by nothingspecial on 2012-04-12
It would still be easier to install the minimal system then add what you want IMHO.

---

### Post by snowpine on 2012-04-12
I believe the following command will uninstall all Ubuntu/Unity components:

```
sudo apt-get remove acpi-support acpid adium-theme-ubuntu aisleriot apg app-install-data app-install-data-partner appmenu-gtk appmenu-gtk3 appmenu-qt apt-xapian-index apturl apturl-common at-spi2-core avahi-autoipd bamfdaemon banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore baobab binfmt-support bluez-alsa bluez-cups bluez-gstreamer branding-ubuntu brasero brasero-cdrkit brasero-common brltty c2esp checkbox checkbox-gtk cli-common compiz compiz-core compiz-gnome compiz-plugins-default compiz-plugins-main-default compizconfig-backend-gconf cups-bsd dc deja-dup dmz-cursor-theme doc-base duplicity dvd+rw-tools empathy empathy-common eog espeak espeak-data evolution-data-server evolution-data-server-common example-content exiv2 firefox firefox-globalmenu firefox-gnome-support foo2zjs gamin gbrainy gcalctool gcc gcc-4.6 gedit gedit-common geoclue geoclue-ubuntu-geoip ghostscript-x ginn gir1.2-atspi-2.0 gir1.2-gconf-2.0 gir1.2-gmenu-3.0 gir1.2-gtksource-3.0 gir1.2-indicate-0.6 gir1.2-launchpad-integration-3.0 gir1.2-peas-1.0 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-wnck-3.0 gnome-accessibility-themes gnome-codec-install gnome-control-center gnome-control-center-data gnome-desktop3-data gnome-font-viewer gnome-games-common gnome-icon-theme-symbolic gnome-mahjongg gnome-media gnome-menus gnome-nettool gnome-online-accounts gnome-orca gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data gnome-utils-common gnomine growisofs gstreamer0.10-alsa gstreamer0.10-gconf gstreamer0.10-plugins-base-apps gstreamer0.10-pulseaudio gstreamer0.10-tools guile-1.8-libs gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter hplip hplip-cups hplip-data hwdata ibus ibus-gtk ibus-gtk3 ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table im-switch indicator-appmenu indicator-datetime indicator-power indicator-session indicator-sound inputattach intel-gpu-tools kerneloops-daemon lftp libappindicator0.1-cil libasound2-plugins libatk-adaptor libatspi2.0-0 libavahi-gobject0 libbamf0 libbamf3-0 libboost-serialization1.46.1 libbrasero-media3-1 libbrlapi0.5 libc-dev-bin libc6-dev libcamel-1.2-29 libcanberra-pulse libcompizconfig0 libcrypt-passwdmd5-perl libdbus-glib1.0-cil libdbus1.0-cil libdbusmenu-qt2 libdconf-dbus-1-0 libdconf-qt0 libdconf0 libdecoration0 libdotconf1.0 libebackend-1.2-1 libebook1.2-12 libecal1.2-10 libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver1.2-15 libedataserverui-3.0-1 libespeak1 libexempi3 libexiv2-10 libfile-copy-recursive-perl libfolks-telepathy25 libfolks25 libgail-3-common libgail-common libgamin0 libgconf2.0-cil libgd2-xpm libgdata-common libgdata1.7-cil libgdata13 libgdiplus libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libglew1.5 libglewmx1.5 libglib2.0-bin libglib2.0-cil libglib2.0-data libgmime-2.4-2 libgmime2.4-cil libgnome-control-center1 libgnome-desktop-3-2 libgnome-media-profiles-3.0-0 libgnome-menu-3-0 libgnome-menu2 libgnome2-common libgnomekbd-common libgnomekbd7 libgnomevfs2-0 libgnomevfs2-common libgoa-1.0-0 libgomp1 libgtk-sharp-beans-cil libgtk-vnc-2.0-0 libgtk2.0-cil libgtkmm-3.0-1 libgtksourceview-3.0-0 libgtksourceview-3.0-common libgtkspell3-0 libgudev1.0-cil libgvnc-1.0-0 libgweather-3-0 libgweather-common libgwibber-gtk2 libgwibber2 libhyphen0 libibus-1.0-0 libidl0 libido3-0.1-0 libjson-glib-1.0-0 liblaunchpad-integration1.0-cil liblightdm-gobject-1-0 liblouis-data liblouis2 libmetacity-private0 libmission-control-plugins0 libmng1 libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-csharp4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil libmono-system-core4.0-cil libmono-system-drawing4.0-cil libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil libmono-zeroconf1.0-cil libmysqlclient16 libmythes-1.2-0 libnotify-bin libnotify0.4-cil libnux-1.0-0 libnux-1.0-common liboauth0 libopencc1 liborbit2 liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 libpeas-1.0-0 libpeas-common libprotobuf7 libprotoc7 libpulse-mainloop-glib0 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtbamf1 libqtcore4 libqtdee2 libqtgconf1 libqtgui4 libquadmath0 libquvi0 libraptor2-0 librasqal3 librdf0 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-writer librest-0.7-0 librsync1 libsane-hpaio libsdl1.2debian-pulseaudio libspeechd2 libspeexdsp1 libstlport4.6ldbl libsyncdaemon-1.0-1 libtaglib2.0-cil libtelepathy-farsight0 libtelepathy-logger2 libtextcat-data libtextcat0 libtotem-plparser17 libtotem0 libubuntuone-1.0-1 libubuntuone1.0-cil libunique-1.0-0 libunity-2d-private0 libunity-core-4.0-4 libunity-misc4 libutempter0 libuuid-perl libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common libwnck-common libwnck22 libxp6 libxres1 libyajl1 libyaml-tiny-perl libzeitgeist-1.0-1 light-themes lightdm linux-libc-dev make media-player-info metacity metacity-common mono-4.0-gac mono-gac mono-runtime mousetweaks mscompress mysql-common nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share notify-osd notify-osd-icons nux-tools onboard oneconf openprinting-ppds overlay-scrollbar pinyin-database pkg-config plymouth-theme-ubuntu-logo protobuf-compiler ptouch-driver pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils pxljr python-brlapi python-configglue python-dateutil python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf python-ibus python-imaging python-indicate python-libproxy python-louis python-openssl python-pam python-papyon python-pexpect python-piston-mini-client python-protobuf python-pyatspi2 python-pyinotify python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno python-virtkey python-webkit python-wnck qdbus qt-at-spi radeontool rastertosag-gdi rdesktop rfkill rtkit sane-utils seahorse shotwell sni-qt software-center speech-dispatcher splix ssh-askpass-gnome syslinux syslinux-common telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-indicator telepathy-logger telepathy-mission-control-5 telepathy-salut thunderbird thunderbird-globalmenu thunderbird-gnome-support tomboy toshset totem totem-common totem-mozilla totem-plugins ttf-opensymbol ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-sso-client ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-gtk ubuntuone-couch ubuntuone-installer unity unity-2d unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-asset-pool unity-common unity-greeter unity-lens-applications unity-lens-files unity-lens-music unity-scope-musicstores unity-services uno-libs3 update-inetd ure usb-creator-common usb-creator-gtk vinagre vino whois wodim xbitmaps xcursor-themes xdg-user-dirs-gtk xdiagnose xfonts-mathml xterm xul-ext-ubufox zeitgeist zeitgeist-core zeitgeist-datahub zeitgeist-extension-fts zenity zenity-common && sudo apt-get install ubuntu-minimal
```

source: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)
If you are using a release other than 11.10 then adjust accordingly.

---

### Post by mörgæs on 2012-04-12
> **nothingspecial said:**
> It would still be easier to install the minimal system then add what you want IMHO.

+1

Try this:
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by Fxy on 2012-04-12
Ok ok thanks for your replies, ima just going to go with the minimal iso as it looks like the easiest option :-p}

---

