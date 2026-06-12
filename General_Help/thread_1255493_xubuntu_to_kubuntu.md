---
title: "xubuntu to kubuntu"
date: 2009-09-01
forum: General Help
---

### Post by tinker88 on 2009-09-01
i currently have xubuntu and windows vista dual booted on my dell xps m1530 and i have a cd for kubuntu. 
 
i would like to take xubuntu completely off and just have kubuntu on here but im not sure how to do any of that.
 
can someone please help me?
 
thanks,
tinker

---

### Post by ubuntu27 on 2009-09-01
Open the [Terminal]("http://www.psychocats.net/ubuntu/terminal") and copy and paste the following command to Remove Xubuntu and install Kubuntu

```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial apport-gtk apturl aumix bluez-gnome brasero catfish cupsys-driver-gutenprint desktop-file-utils dmz-cursor-theme doc-base docbook-xml esound-clients esound-common evince exo-utils file-roller firefox firefox-3.0 firefox-3.0-branding firefox-3.0-gnome-support fortune-mod fortunes-min gamin gcalctool gconf2 gconf2-common gdebi gdm ggzcore-bin gigolo gimp gimp-data gksu gnome-accessibility-themes gnome-app-install gnome-cards-data gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-media gnome-media-common gnome-mime-data gnome-mount gnome-power-manager gnome-screensaver gnome-system-monitor gnome-system-tools gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gstreamer0.10-alsa gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-xfce gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin imagemagick imagemagick-doc jockey-gtk language-selector latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libcroco3 libcryptui0 libdiscid0 libdmx1 libdv4 libebook1.2-9 libecal1.2-7 libedataserver1.2-11 libesd-alsa0 libevdocument1 libevview1 libexo-0.3-0 libfftw3-3 libfreezethaw-perl libgadu3 libgail-common libgail18 libgamin0 libgconf2-4 libgcr0 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglew1.5 libglib-perl libglibmm-2.4-1c2a libgnome-desktop-2-11 libgnome-keyring0 libgnome-media0 libgnome-menu2 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgp11-0 libgsf-1-114 libgsf-1-common libgsf-gnome-1-114 libgtk-vnc-1.0-0 libgtk2-perl libgtkhtml2-0 libgtkmathview0c2a libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0 libidl0 libiec61883-0 libjpeg-progs libkpathsea4 liblaunchpad-integration1 liblink-grammar4 liblircclient0 libmbca0 libmetacity0 libmldbm-perl libnautilus-burn4 libnautilus-extension1 libnet-dbus-perl libnotify-bin libnotify1 libofa0 liboil0.3 liboobs-1-4 liborbit2 libots0 libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libpolkit-gnome0 libpoppler-glib4 libproxy0 libpurple-bin libpurple0 librarian0 librecode0 librsvg2-2 librsvg2-common libscim8c2a libsexy2 libshout3 libsilc-1.1-2 libsoup-gnome2.4-1 libsoup2.4-1 libstartup-notification0 libt1-5 libtagc0 libtdb1 libthunar-vfs-1-2 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libtunepimp5 libuuid-perl libv4l-0 libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwnck-common libwnck22 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr3 link-grammar-dictionaries-en listen metacity-common mobile-broadband-provider-info mousepad mozilla-thunderbird network-manager-gnome notification-daemon onboard orage oss-compat pidgin pidgin-data pidgin-otr policykit-gnome psutils python-cairo python-gconf python-gdata python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-musicbrainz2 python-mutagen python-notify python-ogg python-pkg-resources python-pymad python-pyogg python-pyorbit python-pysqlite2 python-pyvorbis python-rdflib python-sexy python-tunepimp python-virtkey python-vte rarian-compat rss-glx scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images seahorse seahorse-plugins sgml-data software-properties-gtk ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird totem totem-common totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk ubufox ubuntu-gdm-themes update-manager update-notifier vim-runtime vinagre wdiff xbitmaps xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xterm xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xulrunner-1.9 xulrunner-1.9-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop
```


The previous command is for the current version of (X)Ubuntu which is 9.04 (Jaunty). If you are using another version, check out this site:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by QIII on 2009-09-01
My first suggestion:  just get a new paint job.

This is over-simplifying somewhat, but in general:

Ubuntu = Gnome + Ubuntu

Xubuntu = XFCE + Ubuntu

Kubuntu = KDE + Ubuntu

Install KDE and at your next login you will get the choice of XFCE or KDE.

---

### Post by tinker88 on 2009-09-01
how do i install kde? if that is how i decide to go about it ....the main reason why i wanna switch is because the linux side of my computer has messed up sooo badly that i dont think i can ever fix it so i figure i would just clear it and either reinstall xubuntu or install kubuntu to try that flavor out

---

### Post by Lampi on 2009-09-01
is it still possible to let tasksel do the job? from what I recall you could boot into runlevel 2 (better stay outside of X), become root and use good old "tasksel" to give you the choice what desktop environment to install. It worked in Intrepid, i didn't use it along with jaunty

---

### Post by ubuntu27 on 2009-09-01
You can install KDE, Xfce, GNome, etc using amn Package Manager such as Synaptic.

At GDM or KDM (where you login by entering your user-name & password), you can choose which DE to use.

---

