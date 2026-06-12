---
title: "network-manager to be autoremoved?"
date: 2011-08-31
forum: General Help
---

### Post by wecing on 2011-08-31
Today apt-get notified me this:

> The following packages were automatically installed and are no longer required:
  python-bugbuddy xdg-user-dirs-gtk libpcsclite1 usb-modeswitch geoclue
  gtk2-engines-smooth dnsmasq-base tomboy python-evolution ekiga
  libmono-security2.0-cil update-notifier-common libgnome-bluetooth7
  libndesk-dbus1.0-cil libmtp8 libmono-addins-gui0.2-cil gcalctool
  libopal3.6.8 gnome-backgrounds telepathy-gabble gnome-search-tool
  libmono-system2.0-cil tcptraceroute update-notifier baobab
  libfreerdp-plugins-standard python-mako hamster-applet [COLOR="red"]network-manager-gnome[/COLOR]
  libsrtp0 gnome-system-log gucharmap libdiscid0 geoclue-localnet gnome-games
  obexd-client cheese gdebi libgpod-common obex-data-server
  libgnomepanel2.24-cil libmono-corlib2.0-cil cli-common rhythmbox libnm-util1
  libtelepathy-farsight0 libmono-cairo2.0-cil libgexiv2-0 empathy-common
  libcheese-gtk18 libpolkit-gtk-1-0 geoclue-yahoo libndesk-dbus-glib1.0-cil
  usb-modeswitch-data gnome-themes-extras mobile-broadband-provider-info
  evolution-exchange libpcap0.8 transmission-gtk libmono-i18n-west2.0-cil
  libapr1 guile-1.8-libs update-manager-gnome seahorse empathy
  libchamplain-0.4-0 xdg-user-dirs gdebi-core gvfs-bin software-center
  libmono-posix2.0-cil libaprutil1-ldap mono-runtime telepathy-salut libgpod4
  libmono-addins0.2-cil libgeoclue0 libgnome2.24-cil gnome-cards-data
  gnuchess-book gnome-nettool transmission-common gnome-codec-install
  gnome-screenshot shotwell update-manager-core gnome-games-extra-data
  python-webkit gconf-editor libcryptui0 simple-scan python-aptdaemon
  libclutter-gtk-0.10-0 libgee2 network-manager gnome-system-tools
  epiphany-extensions binfmt-support libnm-glib-vpn1 python-gtkglext1
  libgnome-vfs2.0-cil libaprutil1-dbd-sqlite3 libtelepathy-glib0 mono-gac
  python-vte libnm-glib2 gnome-bluetooth gnome-user-share modemmanager
  gconf-defaults-service libglade2.0-cil apache2.2-bin seahorse-plugins
  libopenobex1 libspeexdsp1 cheese-common sound-juicer libart2.0-cil vino
  aptdaemon libglib2.0-cil mono-2.0-gac libgconf2.0-cil python-aptdaemon-gtk
  ppp tcl libapache2-mod-dnssd libmono-sharpzip2.84-cil wpasupplicant
  nautilus-sendto tcl8.4 gedit-plugins liferea libpt2.6.7 remmina-plugin-rdp
  gnome-themes-more media-player-info python-markupsafe libchamplain-gtk-0.4-0
  remmina-plugin-vnc gnome-games-data geoclue-manual libmusicbrainz3-6
  gstreamer0.10-tools liferea-data geoclue-hostip gnome-office gnuchess
  libfreerdp0 fast-user-switch-applet libgtk2.0-cil libssh-4 totem-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugins libaprutil1 libgmime2.4-cil
  remmina-plugin-data libnet1 [COLOR="Red"]freeglut3[/COLOR] nautilus-sendto-empathy
  telepathy-mission-control-5 remmina python-opengl


I feel really confused why apt-get marks these packages as needless.

---

### Post by jfed on 2011-08-31
Sweet mother of beans, I haven't seen anything like that before haha.

When and how exactly did apt notify you of this? Did you try to install a program then out of no where it was just like "Oh by the way I installed like 90 packages"?

---

### Post by jasef on 2011-08-31
The fact it's trying to remove things like network-manager-gnome, software-center, mono, and nautilus plugins, it seems like it's lost a metapackage that depends on them, check that packages like 'gnome-desktop' or 'ubuntu-desktop' are installed. I'm not sure which one it's called currently because I'm on my Windows box, I'll check in a few minutes when I start my laptop.

---

### Post by donato roque on 2011-08-31
This is bogus.

---

### Post by Frogs Hair on 2011-08-31
I have seen this on my first trial of Ubuntu . I started removing packages that I didn't want /use and reached a point where had removed almost the entire desktop and the remaining packages became auto removable .

The solution was to reinstall everything. I decided that if I wanted to strip down Ubuntu like that in the future I would start with a minimal installation .

Checking history in the software center display what you have installed and removed .

---

### Post by wecing on 2011-08-31
I just reinstalled my Debian squeeze(with /home untouched), then fetched some packages like firmware-linux-nonfree and realtek-nonfree.

Maybe I can solve this by using apt-get to install these packages explicitly? However installing gnome-desktop-environment didn't help.

---

