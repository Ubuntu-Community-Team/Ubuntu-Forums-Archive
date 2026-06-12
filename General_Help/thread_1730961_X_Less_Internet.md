---
title: "X Less Internet"
date: 2011-04-16
forum: General Help
---

### Post by linuxyogi on 2011-04-16
Hi,

I sometimes download large files using torrent clients.

The PC I use for the purpose is an old Celeron 2.13, 384MB Ram.

I am running Lucid.

What I want is to run a torrent client without the X Server. This will further minimize the load on the PC. 

I have never used Linux without the GUI except for some admin tasks. 

**Please suggest me a torrent client which can run without the X and how to do this.**

---

### Post by Joe of loath on 2011-04-16
transmission has both a cli and web interface as well as the default GTK interface, and I believe rtorrent is entirely CLI.

---

### Post by linuxyogi on 2011-04-16
> **Joe of loath said:**
> transmission has both a cli and web interface as well as the default GTK interface, and I believe rtorrent is entirely CLI.

Okay but how do I get rid of the GUI ?

By pressing CTRL+ALT+F? .............F then what F1....F2...F3  ?

---

### Post by Joe of loath on 2011-04-16
That just hides it. You'll want to uninstall it.

```
sudo apt-get remove adium-theme-ubuntu aisleriot alacarte app-install-data-partner apport-gtk apt-xapian-index aptdaemon at-spi baobab binfmt-support binutils bluez-gstreamer bogofilter bogofilter-bdb bogofilter-common branding-ubuntu brasero brasero-cdrkit brasero-common brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin desktop-file-utils desktopcouch dmz-cursor-theme doc-base empathy empathy-common eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl espeak espeak-data evince evince-common evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content file-roller firefox firefox-branding firefox-gnome-support gamin gbrainy gcalctool gcc gcc-4.4 gconf-defaults-service gconf-editor gconf2 gconf2-common gdm gdm-guest-session gedit gedit-common gksu gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-dictionary gnome-disk-utility gnome-doc-utils gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-power-manager gnome-screensaver gnome-screenshot gnome-search-tool gnome-session gnome-session-bin gnome-session-canberra gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnome-utils-common gnomine gstreamer0.10-alsa gstreamer0.10-gnonlin gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-fuse gwibber gwibber-service humanity-icon-theme hwdata ibus ibus-gtk ibus-pinyin ibus-pinyin-db-android ibus-pinyin-db-open-phrase ibus-table indicator-applet indicator-applet-session indicator-application indicator-me indicator-messages indicator-session indicator-sound jockey-gtk language-selector launchpad-integration libappindicator0.1-cil libappindicator1 libart-2.0-2 libart2.0-cil libatspi1.0-0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media1 libburn4 libc-dev-bin libc6-dev libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio10 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-2 libcroco3 libcryptui0 libcurl3 libdbusmenu-gtk1 libdconf0 libdecoration0 libdesktopcouch-glib-1.0-2 libdmapsharing2 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8 libegroupwise1.2-13 libept1 libespeak1 libevdocument3 libevent-1.4-2 libevolution libevview3 libexempi3 libfolks-telepathy0 libfolks0 libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata7 libgdict-1.0-6 libgdu-gtk0 libgdu0 libgee2 libgexiv2-0 libgksu2-0 libglade2-0 libglade2.0-cil libgladeui-1-9 libglib-perl libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libgmime-2.4-2 libgmime2.4-cil libgnome-bluetooth8 libgnome-desktop-2-17 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoocanvas-common libgoocanvas3 libgp11-0 libgsl0ldbl libgssdp-1.0-2 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-3 libgupnp-igd-1.0-3 libgvfscommon0 libgweather-common libgweather1 libgwibber0 libibus2 libidl0 libido-0.1-0 libiec61883-0 libindicate-gtk2 libindicator1 libisofs6 libjson-glib-1.0-0 libkpathsea5 liblaunchpad-integration1 liblaunchpad-integration1.0-cil liblircclient0 liblouis-data liblouis2 liblua5.1-0 libmetacity-private0 libmission-control-plugins0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil libmono-management2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-system2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboobs-1-5 libopencc1 liborbit2 liborc-0.4-0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpolkit-gtk-1-0 libpoppler-glib5 libportaudio2 libprotobuf6 libprotoc6 libproxy0 libpurple-bin libpurple0 librarian0 librsvg2-2 librsvg2-common libsctp1 libsdl1.2debian-pulseaudio libshout3 libsigc++-2.0-0c2a libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libstartup-notification0 libsyncdaemon-1.0-1 libt1-5 libtelepathy-farsight0 libtelepathy-glib0 libtelepathy-logger1 libtie-ixhash-perl libtotem-plparser17 libubuntuone-1.0-1 libunique-1.0-0 libupower-glib1 libuuid-perl libvala-0.10-0 libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-event1 libxklavier16 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 light-themes linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-headers-generic linux-libc-dev lksctp-tools lzma manpages-dev media-player-info metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-csharp-shell mono-gac mono-gmcs mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-sendto-empathy nautilus-share network-manager-gnome network-manager-pptp-gnome notify-osd notify-osd-icons onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pinyin-database pitivi pkg-config plymouth-theme-ubuntu-logo policykit-1-gnome protobuf-compiler pulseaudio-module-gconf python-appindicator python-aptdaemon python-aptdaemon-gtk python-argparse python-avahi python-brlapi python-configglue python-couchdb python-crypto python-desktopcouch-records python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-gtkspell python-ibus python-indicate python-launchpad-integration python-libproxy python-libxml2 python-louis python-mako python-markupsafe python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pycurl python-pygoocanvas python-pyinotify python-pyorbit python-rdflib python-serial python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit python-wnck python-xapian quadrapassel rarian-compat rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store screen-resolution-extra screensaver-default-images scrollkeeper seahorse sessioninstaller shotwell simple-scan software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-logger telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono ubuntu-sounds ubuntu-sso-client ubuntu-system-service ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome update-manager update-notifier upower usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xscreensaver-data xscreensaver-gl xsltproc xul-ext-ubufox xulrunner-1.9.2 yelp zenity
```

---

### Post by linuxyogi on 2011-04-16
> **Joe of loath said:**
> That just hides it. You'll want to uninstall it.


I don't really want to uninstall it. I may need it later. 

Is there a way to **"stop"** it ? and then when needed **"start"** it ?

---

### Post by WorMzy on 2011-04-16
```
sudo /etc/init.d/gdm stop
```

or possibly

```
sudo service gdm stop
```

replace stop with start for the reverse effect.

NOTE: This is assuming you're using the default Ubuntu installation. For Kubuntu, I believe that you should stop kdm instead. For Xubuntu, I think it's still gdm. No idea about lubuntu; probably uses a non-daemonized display manager, like slim, which may need to be "kill"ed with pkill or killall.

---

### Post by linuxyogi on 2011-04-16
> **WorMzy said:**
> ```
sudo /etc/init.d/gdm stop
```or possibly

```
sudo service gdm stop
```replace stop with start for the reverse effect.

Tried both didn't work.

---

### Post by WorMzy on 2011-04-16
I updated my post. Have you installed kubuntu?

---

### Post by ~Plue on 2011-04-16
edited

---

### Post by linuxyogi on 2011-04-16
> **WorMzy said:**
> I updated my post. Have you installed kubuntu?

No, actually I am using [BodhiLinux]("http://www.google.co.in/url?sa=t&source=web&cd=1&ved=0CB8QFjAA&url=http%3A%2F%2Fwww.bodhilinux.com%2F&rct=j&q=bodhilinux&ei=r--pTcDRC5KK0QH_2vT4CA&usg=AFQjCNEGgYjyW0UeBTke62WVuBobQ2sbIQ&cad=rja") which is based on Ubuntu 10.04. It uses the Enlightenment Desktop.

---

### Post by linuxyogi on 2011-04-16
> **~Plue said:**
> try[FONT=monospace]
[/FONT] 	Code:
 	sudo initctl stop gdm 



Not working.

---

### Post by Joe of loath on 2011-04-16
Enlightenment, that's why none of these are working.

Unfortunately I don't know anything about enlightenment.

---

### Post by linuxyogi on 2011-04-16
> **Joe of loath said:**
> Enlightenment, that's why none of these are working.

Unfortunately I don't know anything about enlightenment.

No problem. Thanks for trying.

---

### Post by linuxyogi on 2011-04-16
Anyone ..............?

---

### Post by ~Plue on 2011-04-16
bodhi uses lxdm according to their [about page]("http://www.bodhilinux.com/about.html")
try replacing gdm with lxdm with the previous command

//dunno much about it so cant help you any further than that. sorry

---

### Post by WorMzy on 2011-04-16
> **linuxyogi said:**
> No, actually I am using [BodhiLinux]("http://www.google.co.in/url?sa=t&source=web&cd=1&ved=0CB8QFjAA&url=http%3A%2F%2Fwww.bodhilinux.com%2F&rct=j&q=bodhilinux&ei=r--pTcDRC5KK0QH_2vT4CA&usg=AFQjCNEGgYjyW0UeBTke62WVuBobQ2sbIQ&cad=rja") which is based on Ubuntu 10.04. It uses the Enlightenment Desktop.

Ah. Not familiar with that one, sorry.

You may get better support on one of the [Enlightenment]("http://www.enlightenment.org/p.php?p=support&l=en") or [Bodhi]("http://www.bodhilinux.com/getsupport.html") support channels.

---

### Post by linuxyogi on 2011-04-16
I went to both  the IRCs i.e. Bodhi support and Enlightenment.

A guy responded at the Bodhi's IRC but he didn't have the solution.

No one responded at the Enlightenment's IRC


Anyways, lets see if someone can help.[-o<

---

### Post by Slim Odds on 2011-04-16
> **linuxyogi said:**
> Not working.

You can't do this FROM THE GUI.

You need to do the Ctrl-Alt-F1 to get to a console, then sudo /etc/init.d/gdm stop.

---

