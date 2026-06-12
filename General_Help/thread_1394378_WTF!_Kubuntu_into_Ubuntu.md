---
title: "WTF?! Kubuntu into Ubuntu?"
date: 2010-01-30
forum: General Help
---

### Post by ApocoLypTus on 2010-01-30
WTF? Okay. So i was just rebooting my computer when all of a sudden i went into Kubuntu 9.10 and now it is Ubuntu?

And when i login.. Its now Ubuntu. and a error pops up. It was doing a disk check before this happened and it just blew up into Ubuntu? WTF?

```
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?
Dont Delete | Delete
```

HELP!!!!!

---

### Post by ApocoLypTus on 2010-01-30
OMG! What is going on?

---

### Post by Leppie on 2010-01-30
are you sure you booted into kubuntu? did you not also have ubuntu installed on your machine?

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> are you sure you booted into kubuntu? did you not also have ubuntu installed on your machine?

100% sure that i booted into Kubuntu. I have never even tried to instert a Ubuntu 9.10 CD. Ubuntu is not installed.

---

### Post by Leppie on 2010-01-30
so what did yo install before the reboot?

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> so what did yo install before the reboot?

AWN. And when i restarted, a disk check thing came up when i tried to boot into Kubuntu. I let that disk check do its thing. And it popped up in Ubuntu.

---

### Post by Leppie on 2010-01-30
have you tried booting into the recovery console and removing awn?

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> have you tried booting into the recovery console and removing awn?

Nope... But i dont think that AWN has anythign to do with it.. I think that it was the disk Check thingy when the Kubuntu loading sign comes...

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> Nope... But i dont think that AWN has anythign to do with it.. I think that it was the disk Check thingy when the Kubuntu loading sign comes...
disk checking doesn't install stuff onto your system...

---

### Post by wojox on 2010-01-30
What happens when you run this in the terminal:

```
dpkg -l | grep gnome
```

---

### Post by tom.swartz07 on 2010-01-30
> **ApocoLypTus said:**
> Nope... But i dont think that AWN has anythign to do with it.. I think that it was the disk Check thingy when the Kubuntu loading sign comes...

nah- check disk has nothing to do with your desktop manager.


try running 
```
sudo apt-get purge kubuntu-desktop ubuntu-desktop && sudo apt-get install kubuntu-desktop
```

---

### Post by ApocoLypTus on 2010-01-30
> **wojox said:**
> What happens when you run this in the terminal:

```
dpkg -l | grep gnome
```

```
ii  gnome-about                          1:2.28.1-0ubuntu3                          The GNOME about box                                                         
ii  gnome-applets                        2.28.0-0ubuntu2                            Various applets for GNOME 2 panel - binary f                                
ii  gnome-applets-data                   2.28.0-0ubuntu2                            Various applets for GNOME 2 panel - data fil                                
ii  gnome-control-center                 1:2.28.1-0ubuntu1                          utilities to configure the GNOME desktop                                    
ii  gnome-desktop-data                   1:2.28.1-0ubuntu3                          Common files for GNOME 2 desktop apps                                       
ii  gnome-doc-utils                      0.18.0-0ubuntu1                            a collection of documentation utilities for                                 
ii  gnome-icon-theme                     2.28.0-0ubuntu1                            GNOME Desktop icon theme                                                    
ii  gnome-keyring                        2.28.1-0ubuntu1                            GNOME keyring services (daemon and tools)                                   
ii  gnome-media                          2.28.1-0ubuntu1                            GNOME media utilities                                                       
ii  gnome-media-common                   2.28.1-0ubuntu1                            GNOME media utilities - common files                                        
ii  gnome-menus                          2.28.0.1-0ubuntu1                          an implementation of the freedesktop menu sp                                
ii  gnome-mime-data                      2.18.0-1                                   base MIME and Application database for GNOME                                
ii  gnome-panel                          1:2.28.0-0ubuntu6                          launcher and docking facility for GNOME                                     
ii  gnome-panel-data                     1:2.28.0-0ubuntu6                          common files for the GNOME Panel                                            
ii  gnome-session                        2.28.0-0ubuntu5                            The GNOME Session Manager                                                   
ii  gnome-session-bin                    2.28.0-0ubuntu5                            The GNOME Session Manager - Minimal runtime                                 
ii  gnome-settings-daemon                2.28.1-0ubuntu2                            GNOME settings daemon                                                       
ii  gnome-system-monitor                 2.28.0-0ubuntu1                            Process viewer and system resource monitor f                                
ii  gnome-user-guide                     2.28.0+git20090921ubuntu2                  GNOME user's guide                                                          
ii  libgnome-desktop-2-11                1:2.28.1-0ubuntu3                          Utility library for loading .desktop files -                                
ii  libgnome-keyring0                    2.28.1-0ubuntu1                            GNOME keyring services library                                              
ii  libgnome-media0                      2.28.1-0ubuntu1                            runtime libraries for the GNOME media utilit                                
ii  libgnome-menu2                       2.28.0.1-0ubuntu1                          an implementation of the freedesktop menu sp                                
ii  libgnome-window-settings1            1:2.28.1-0ubuntu1                          Utility library for getting window manager s                                
ii  libgnome2-0                          2.28.0-0ubuntu3                            The GNOME library - runtime files                                           
ii  libgnome2-canvas-perl                1.002-2                                    Perl interface to the GNOME canvas library                                  
ii  libgnome2-common                     2.28.0-0ubuntu3                            The GNOME library - common files                                            
ii  libgnome2-perl                       1.042-2                                    Perl interface to the GNOME libraries                                       
ii  libgnome2-vfs-perl                   1.081-1                                    Perl interface to the 2.x series of the GNOM
ii  libgnomecanvas2-0                    2.26.0-1                                   A powerful object-oriented display - runtime
ii  libgnomecanvas2-common               2.26.0-1                                   A powerful object-oriented display - common
ii  libgnomekbd-common                   2.28.0-0ubuntu2                            GNOME library to manage keyboard configurati
ii  libgnomekbd4                         2.28.0-0ubuntu2                            GNOME library to manage keyboard configurati
ii  libgnomekbdui4                       2.28.0-0ubuntu2                            User interface library for libgnomekbd - sha
ii  libgnomeui-0                         2.24.2-1                                   The GNOME libraries (User Interface) - runti
ii  libgnomeui-common                    2.24.2-1                                   The GNOME libraries (User Interface) - commo
ii  libgnomevfs2-0                       1:2.24.2-1ubuntu1                          GNOME Virtual File System (runtime libraries
ii  libgnomevfs2-common                  1:2.24.2-1ubuntu1                          GNOME Virtual File System (common files)
ii  libgnomevfs2-extra                   1:2.24.2-1ubuntu1                          GNOME Virtual File System (extra modules)
ii  libpam-gnome-keyring                 2.28.1-0ubuntu1                            PAM module to unlock the GNOME keyring upon
ii  libsoup-gnome2.4-1                   2.28.1-2                                   an HTTP library implementation in C -- GNOME
ii  policykit-1-gnome                    0.94-1+1git.230873                         GNOME authentication agent for PolicyKit-1
ii  python-gnome2                        2.28.0-0ubuntu1                            Python bindings for the GNOME desktop enviro
ii  python-gnomeapplet                   2.28.0-0ubuntu1                            Python bindings for the GNOME panel applet l
ii  python-gnomecanvas                   2.28.0-0ubuntu1                            Python bindings for gnomecanvas (debug exten
ii  python-gnomedesktop                  2.28.0-0ubuntu1                            Python bindings for the GNOME desktop librar
```I'm GNOMED!?

> **tom.swartz07 said:**
> nah- check disk has nothing to do with your desktop manager.


try running 
```
sudo apt-get purge kubuntu-desktop ubuntu-desktop && sudo apt-get install kubuntu-desktop
```
 
Okay. So i did that command what now?

---

### Post by tom.swartz07 on 2010-01-30
> **ApocoLypTus said:**
>  
Okay. So i did that command what now?

Should be fine after you restart?

Check out the docs here to assure you have a full KDE system:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by tom.swartz07 on 2010-01-30
specifically, you should just run this big command:
```
sudo apt-get remove aisleriot alacarte app-install-data-partner apport-gtk aptdaemon at-spi binfmt-support brasero brltty-x11 capplets-data checkbox checkbox-gtk cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper compizconfig-backend-gconf computer-janitor computer-janitor-gtk couchdb-bin dcraw desktop-file-utils desktopcouch devicekit-power dmz-cursor-theme doc-base docbook-xml empathy empathy-doc eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl esound-clients esound-common espeak espeak-data evince evolution evolution-common evolution-couchdb evolution-data-server evolution-data-server-common evolution-documentation-en evolution-exchange evolution-indicator evolution-plugins evolution-webcal example-content f-spot file-roller firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gamin gcalctool gconf-defaults-service gconf-editor gconf2 gconf2-common gdebi gdm gdm-guest-session gedit gedit-common ggzcore-bin gimp gimp-data gksu glchess glines gnect gnibbles gnobots2 gnome-about gnome-accessibility-themes gnome-applets gnome-applets-data gnome-blackjack gnome-bluetooth gnome-codec-install gnome-control-center gnome-desktop-data gnome-disk-utility gnome-doc-utils gnome-games gnome-games-common gnome-icon-theme gnome-keyring gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu gnome-user-guide gnome-utils gnometris gnomine gnotravex gnotski gstreamer0.10-alsa gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtali gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-theme humanity-icon-theme iagno ibus ibus-gtk ibus-m17n ibus-table indicator-applet indicator-applet-session indicator-messages indicator-session jockey-gtk language-selector launchpad-integration libanthy0 libart-2.0-2 libart2.0-cil libasound2-plugins libatspi1.0-0 libaudiofile0 libavahi-glib1 libavahi-gobject0 libavahi-ui0 libavc1394-0 libbabl-0.0-0 libbeagle1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrasero-media0 libcairo-perl libcairomm-1.0-1 libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra-pulse libcanberra0 libcdio-cdda0 libcdio-paranoia0 libcdio7 libclutter-1.0-0 libclutter-gtk-0.10-0 libcompizconfig0 libcouchdb-glib-1.0-1 libcroco3 libcryptui0 libcurl3 libdbusmenu-glib0 libdbusmenu-gtk0 libdecoration0 libdevkit-power-gobject1 libdotconf1.0 libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libempathy-common libempathy-gtk-common libempathy-gtk28 libempathy30 libesd-alsa0 libespeak1 libevdocument1 libevent-1.4-2 libevview1 libexchange-storage1.2-3 libexempi3 libflickrnet2.2-cil libfreezethaw-perl libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgcr0 libgd2-xpm libgdata-common libgdata-google1.2-1 libgdata1.2-1 libgdata5 libgdict-1.0-6 libgdiplus libgdu-gtk0 libgdu0 libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0 libglade2.0-cil libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1 libglitz1 libgmime-2.0-2a libgmime-2.4-2 libgmime2.2a-cil libgnome-bluetooth7 libgnome-desktop-2-11 libgnome-keyring0 libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomekbdui4 libgnomepanel2.24-cil libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgsf-1-114 libgsf-1-common libgssdp-1.0-1 libgstfarsight0.10-0 libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-cil libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap7 libgupnp-1.0-2 libgupnp-igd-1.0-2 libgvfscommon0 libgweather-common libgweather1 libibus1 libidl0 libiec61883-0 libindicate-gtk1 libjson-glib-1.0-0 libkpathsea4 liblaunchpad-integration1 liblircclient0 liblouis-data liblouis0 liblpint-bonobo0 libm17n-0 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnice0 libnotify1 liboil0.3 liboobs-1-4 liborbit2 libotf0 libpam-gnome-keyring libpanel-applet2-0 libpango-perl libpangomm-1.4-1 libpisock9 libpisync1 libpolkit-agent-1-0 libpolkit-gtk-1-0 libpoppler-glib4 libportaudio2 libprotobuf3 libproxy0 libpst4 libpulse-browse0 libpulse-mainloop-glib0 libpurple-bin libpurple0 librarian0 libraw1394-11 librsvg2-2 librsvg2-common libsctp1 libsexy2 libshout3 libsilc-1.1-2 libsilcclient-1.1-3 libsoup-gnome2.4-1 libsoup2.4-1 libspeechd2 libspeexdsp1 libsqlite0 libstartup-notification0 libtdb1 libtelepathy-farsight0 libtelepathy-glib0 libtie-ixhash-perl libtotem-plparser12 libtrackerclient0 libunique-1.0-0 libuuid-perl libvisual-0.4-0 libvisual-0.4-plugins libvte-common libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7-gtk libwnck-common libwnck22 libxcb-atom1 libxcb-aux0 libxcb-event1 libxml-twig-perl libxml-xpath-perl libxres1 libzephyr4 lksctp-tools m17n-contrib m17n-db media-player-info mesa-utils metacity metacity-common mobile-broadband-provider-info mono-2.0-gac mono-gac mono-runtime mousetweaks nautilus nautilus-data nautilus-sendto nautilus-share network-manager-gnome notification-daemon notify-osd notify-osd-icons obexd-client onboard openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-style-human pkg-config policykit-1-gnome protobuf-compiler pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-aptdaemon python-aptdaemon-gtk python-avahi python-brlapi python-cairo python-configglue python-couchdb python-crypto python-desktopcouch python-desktopcouch-records python-fstab python-gconf python-glade2 python-gmenu python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomekeyring python-gst0.10 python-gtk2 python-gtksourceview2 python-ibus python-launchpad-integration python-libxml2 python-louis python-notify python-openssl python-pam python-papyon python-protobuf python-pyatspi python-pyinotify python-pyorbit python-rdflib python-rsvg python-serial python-sexy python-speechd python-telepathy python-twisted-bin python-twisted-core python-twisted-names python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol python-virtkey python-vte python-webkit rarian-compat rhythmbox same-gnome screen-resolution-extra screensaver-default-images seahorse sgml-data software-center software-properties-gtk speech-dispatcher ssh-askpass-gnome synaptic system-config-printer-gnome system-tools-backends telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-mission-control-5 telepathy-salut tomboy totem totem-common totem-mozilla totem-plugins transmission-common transmission-gtk tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome update-manager update-notifier usb-creator-gtk vinagre vino whois xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xsplash xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp zenity && sudo apt-get install kubuntu-desktop

```

---

### Post by Leppie on 2010-01-30
reboot...

---

### Post by ApocoLypTus on 2010-01-30
> **tom.swartz07 said:**
> Should be fine after you restart?

Check out the docs here to assure you have a full KDE system:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Will it remove all my stuff? Cuz by what the terminal says it's removing all my stuff.

---

### Post by tom.swartz07 on 2010-01-30
> **ApocoLypTus said:**
> Will it remove all my stuff? Cuz by what the terminal says it's removing all my stuff.

Yeah- its removing all of the Gnome applications. Thats just what you said you wanted? 

It will remove all of the gnome apps and then install all of the kde ones

---

### Post by ApocoLypTus on 2010-01-30
> **tom.swartz07 said:**
> Yeah- its removing all of the Gnome applications. Thats just what you said you wanted? 

It will remove all of the gnome apps and then install all of the kde ones

Thats fine. Thanks it worked. But what did i do wrong? What caused the Ubuntu "takeover"?

---

### Post by tom.swartz07 on 2010-01-30
> **ApocoLypTus said:**
> Thats fine. Thanks it worked. But what did i do wrong? What caused the Ubuntu "takeover"?

Not certain to say- apparently you installed something that needed Ubuntu-desktop, and it put it on your system!

glad its fixed!

---

### Post by ApocoLypTus on 2010-01-30
> **tom.swartz07 said:**
> Not certain to say- apparently you installed something that needed Ubuntu-desktop, and it put it on your system!

glad its fixed!

So it was AWN! Thanks for the fix guys.. Scared that i have been Ubuntuized. :D. So is there any type of Dock that will work with Kubuntu? And not f it up like AWN?

Oh and also a x64.

---

### Post by ApocoLypTus on 2010-01-30
Uhhh i was trying to install Synaptic and this came up... These look like the same files i was trying to delete when i had the GNOME problem. Should i continue the install of Synaptic? Or will it f it up like AWN?

```
ander@xander-desktop:~$ sudo apt-get install synaptic
Reading package lists... Done                         
Building dependency tree                              
Reading state information... Done                     
The following packages were automatically installed and are no longer required:                                               
  bzrtools python-awn-trunk libdesktop-agnostic-fdo-glib       
  python-libdesktop-agnostic xdotool                           
  libdesktop-agnostic-vfs-gio libdesktop-agnostic0             
  libawn1-trunk bzr libgtkglext1 python-chardet                
  python-utidylib python-gdata python-feedparser               
  python-dateutil                                              
Use 'apt-get autoremove' to remove them.                       
The following extra packages will be installed:                
  docbook-xml esound-clients esound-common gamin gconf2        
  gconf2-common gksu gnome-keyring gnome-mime-data gvfs        
  gvfs-backends launchpad-integration libart-2.0-2             
  libaudiofile0 libavahi-glib1 libbonobo2-0 libbonobo2-common  
  libbonoboui2-0 libbonoboui2-common libcairo-perl
  libcdio-cdda0 libcdio-paranoia0 libcdio7 libesd-alsa0
  libgail-common libgail18 libgamin0 libgconf2-4 libgcr0
  libgdu0 libgksu2-0 libglade2-0 libglib-perl
  libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgp11-0 libgtk2-perl libgtop2-7
  libgtop2-common libgvfscommon0 libidl0
  liblaunchpad-integration1 liborbit2 libpam-gnome-keyring
  libpango-perl libpolkit-agent-1-0 libproxy0 librarian0
  libsoup-gnome2.4-1 libsoup2.4-1 libstartup-notification0
  libvte-common libvte9 libxcb-atom1 libxcb-aux0
  libxcb-event1 policykit-1-gnome python-cairo python-glade2
  python-gtk2 rarian-compat sgml-data software-properties-gtk
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide
  gconf-defaults-service libbonobo2-bin esound desktop-base
  gnome-icon-theme libgnomevfs2-bin libgtk2-perl-doc
  librsvg2-common python-gtk2-doc python-numpy perlsgml
  doc-html-w3 opensp dwww menu deborphan
The following NEW packages will be installed:
  docbook-xml esound-clients esound-common gamin gconf2
  gconf2-common gksu gnome-keyring gnome-mime-data gvfs
  gvfs-backends launchpad-integration libart-2.0-2
  libaudiofile0 libavahi-glib1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libcairo-perl
  libcdio-cdda0 libcdio-paranoia0 libcdio7 libesd-alsa0
  libgail-common libgail18 libgamin0 libgconf2-4 libgcr0
  libgdu0 libgksu2-0 libglade2-0 libglib-perl
  libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgp11-0 libgtk2-perl libgtop2-7
  libgtop2-common libgvfscommon0 libidl0
  liblaunchpad-integration1 liborbit2 libpam-gnome-keyring
  libpango-perl libpolkit-agent-1-0 libproxy0 librarian0
  libsoup-gnome2.4-1 libsoup2.4-1 libstartup-notification0
  libvte-common libvte9 libxcb-atom1 libxcb-aux0
  libxcb-event1 policykit-1-gnome python-cairo python-glade2
  python-gtk2 rarian-compat sgml-data software-properties-gtk
  synaptic
0 upgraded, 75 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/13.4MB of archives.
After this operation, 83.1MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> So it was AWN! Thanks for the fix guys.. Scared that i have been Ubuntuized. :D. So is there any type of Dock that will work with Kubuntu? And not f it up like AWN?

Oh and also a x64.
i think cairo dock should work with kde

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> Uhhh i was trying to install Synaptic and this came up... These look like the same files i was trying to delete when i had the GNOME problem. Should i continue the install of Synaptic? Or will it f it up like AWN?
AFAIK synaptic is a Gnome application, so will depend on gnome libraries (hence probably will install gnome if using kde).

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> AFAIK synaptic is a Gnome application, so will depend on gnome libraries (hence probably will install gnome if using kde).

So it is not safe to install?

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> So it is not safe to install?
as i said, i suspect it will install gnome as well.
but you can actually select which DE to use at the login screen...

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> as i said, i suspect it will install gnome as well.
but you can actually select which DE to use at the login screen...

What is the DE? Distro? Like Kubuntu and Ubunutu? How do you do that? So it isn't safe to install Synaptic...

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> What is the DE? Distro? Like Kubuntu and Ubunutu? How do you do that? So it isn't safe to install Synaptic...
DE = Desktop Environment.
i do not know what login screen you have, but normally it should have something like "options" and/or "session". you should be able to change the desktop environment there.

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> DE = Desktop Environment.
i do not know what login screen you have, but normally it should have something like "options" and/or "session". you should be able to change the desktop environment there.

oo... So. I can install Synaptic or anything else. But i would have to log off and go to KDE.

---

### Post by Leppie on 2010-01-30
> **ApocoLypTus said:**
> oo... So. I can install Synaptic or anything else. But i would have to log off and go to KDE.
well, if you're already in kde no need to change.
but if you're in gnome, you could log off and then change to kde at the login screen and log back in.

---

### Post by ApocoLypTus on 2010-01-30
> **Leppie said:**
> well, if you're already in kde no need to change.
but if you're in gnome, you could log off and then change to kde at the login screen and log back in.

Okay. That makes perfect sense. So i can install it.

Thank you for all your help.

---

### Post by Leppie on 2010-01-30
no worries, glad to help :)

---

