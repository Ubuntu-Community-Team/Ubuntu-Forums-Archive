---
title: "Avant Window Navigator installs 200MB of packages?"
date: 2010-08-08
forum: General Help
---

### Post by xXxBlender3DxXx on 2010-08-08
I am running Kubuntu 10.10 (Kubuntu 10.04 -> Maverick -> Strip out most Ubuntu components) and whenever I install AWN, it gives me a HUGE list of packages, including Evolution, and a bunch more Ubuntu-y things...

Is there a way to remove dependencies from a package? This one depends (I think) on ubuntu-desktop.

Here is my apt-get:
```
eading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alacarte awn-applets-c-core awn-applets-python-core awn-settings capplets-data
  desktop-file-utils esound-clients esound-common evolution-data-server
  evolution-data-server-common gamin gnome-about gnome-applets gnome-applets-data
  gnome-control-center gnome-desktop-data gnome-doc-utils gnome-icon-theme gnome-media
  gnome-media-common gnome-menus gnome-mime-data gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-session-bin gnome-settings-daemon
  gnome-system-monitor gnome-user-guide gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gvfs gvfs-backends indicator-applet
  indicator-application indicator-messages indicator-sound launchpad-integration
  libappindicator0 libart-2.0-2 libasound2-plugins libaudiofile0 libavahi-glib1 libavc1394-0
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairomm-1.0-1
  libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0
  libcdio-paranoia0 libcdio10 libcroco3 libdbusmenu-gtk1 libdv4 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8
  libegroupwise1.2-13 libesd0 libexempi3 libgail18 libgamin0 libgdata-google1.2-1 libgdata1.2-1
  libgdu0 libgksu2-0 libglib2.0-data libglibmm-2.4-1c2a libgnome-desktop-2-17 libgnome-media0
  libgnome-menu2 libgnome-window-settings1 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common
  libgtkmm-2.4-1c2a libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common
  libgweather1 libido-0.1-0 libiec61883-0 libindicator0 libjson-glib-1.0-0
  liblaunchpad-integration1 libmetacity-private0 libnautilus-extension1 libnotify1
  libpanel-applet2-0 libpangomm-1.4-1 libproxy0 libpulse-browse0 librarian0 librsvg2-2
  librsvg2-common libshout3 libsoup-gnome2.4-1 libsoup2.4-1 libspeexdsp1
  libstartup-notification0 libtdb1 libunique-1.0-0 libupower-glib1 libvisual-0.4-0
  libvisual-0.4-plugins libvte-common libvte9 libwnck-common libwnck22 libxcb-aux0               
  libxcb-event1 libxres1 metacity metacity-common mousetweaks nautilus nautilus-data             
  policykit-1-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils   
  python-awn python-awn-extras python-cairo python-gconf python-glade2 python-gmenu              
  python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomedesktop python-gst0.10         
  python-gtk2 python-gweather python-libxml2 python-notify python-pyorbit python-rsvg            
  python-vobject rarian-compat rtkit screen-resolution-extra scrollkeeper ubuntu-system-service  
  upower xsltproc xulrunner-1.9.2 yelp zenity                                                    
Suggested packages:                                                                              
  awn-applets-c-extras gconf-editor awn-applets-python-extras evolution                          
  evolution-data-server-dbg tomboy gnome-netstatus-applet deskbar-applet cpufrequtils            
  gnome-screensaver xscreensaver gstreamer0.10-alsa gstreamer0.10-audiosink gnome2-user-guide    
  epiphany-browser menu-xdg desktop-base konqueror libbonobo2-bin libcanberra-pulse libdv-bin    
  esound libgnomevfs2-bin librsvg2-bin gnome-themes eog evince pdf-viewer gnome-app-install      
  totem mp3-decoder brasero nautilus-cd-burner pavumeter paman paprefs python-gnomekeyring       
  python-gnome2-desktop python-gnome2-doc python-gtk2-doc python-gst0.10-dev python-gst0.10-dbg  
  python-numpy python-pyorbit-dbg
The following NEW packages will be installed:
  alacarte avant-window-navigator awn-applets-c-core awn-applets-python-core awn-settings
  capplets-data desktop-file-utils esound-clients esound-common evolution-data-server
  evolution-data-server-common gamin gnome-about gnome-applets gnome-applets-data
  gnome-control-center gnome-desktop-data gnome-doc-utils gnome-icon-theme gnome-media
  gnome-media-common gnome-menus gnome-mime-data gnome-panel gnome-panel-data
  gnome-power-manager gnome-session gnome-session-bin gnome-settings-daemon
  gnome-system-monitor gnome-user-guide gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-x gvfs gvfs-backends indicator-applet
  indicator-application indicator-messages indicator-sound launchpad-integration
  libappindicator0 libart-2.0-2 libasound2-plugins libaudiofile0 libavahi-glib1 libavc1394-0
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairomm-1.0-1
  libcamel1.2-14 libcanberra-gtk-module libcanberra-gtk0 libcanberra0 libcdio-cdda0
  libcdio-paranoia0 libcdio10 libcroco3 libdbusmenu-gtk1 libdv4 libebackend1.2-0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8
  libegroupwise1.2-13 libesd0 libexempi3 libgail18 libgamin0 libgdata-google1.2-1 libgdata1.2-1
  libgdu0 libgksu2-0 libglib2.0-data libglibmm-2.4-1c2a libgnome-desktop-2-17 libgnome-media0
  libgnome-menu2 libgnome-window-settings1 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomekbd-common libgnomekbd4 libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common
  libgtkmm-2.4-1c2a libgtop2-7 libgtop2-common libgucharmap7 libgvfscommon0 libgweather-common
  libgweather1 libido-0.1-0 libiec61883-0 libindicator0 libjson-glib-1.0-0
  liblaunchpad-integration1 libmetacity-private0 libnautilus-extension1 libnotify1
  libpanel-applet2-0 libpangomm-1.4-1 libproxy0 libpulse-browse0 librarian0 librsvg2-2
  librsvg2-common libshout3 libsoup-gnome2.4-1 libsoup2.4-1 libspeexdsp1
  libstartup-notification0 libtdb1 libunique-1.0-0 libupower-glib1 libvisual-0.4-0
  libvisual-0.4-plugins libvte-common libvte9 libwnck-common libwnck22 libxcb-aux0
  libxcb-event1 libxres1 metacity metacity-common mousetweaks nautilus nautilus-data
  policykit-1-gnome pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils
  python-awn python-awn-extras python-cairo python-gconf python-glade2 python-gmenu
  python-gnome2 python-gnomeapplet python-gnomecanvas python-gnomedesktop python-gst0.10
  python-gtk2 python-gweather python-libxml2 python-notify python-pyorbit python-rsvg
  python-vobject rarian-compat rtkit screen-resolution-extra scrollkeeper ubuntu-system-service
  upower xsltproc xulrunner-1.9.2 yelp zenity
0 upgraded, 175 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/48.9MB of archives.
After this operation, 272MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Also, (I think it's a problem with Maverick), my hard disk stops spinning randomly. Then, when I right click, Kubuntu freezes, the hard disk spins up again, and it continues until I stop moving the mouse.

Thanks!

---

### Post by linux18 on 2010-08-08
there is no easy way around dependancies unless you know exactly which packages are needed. 
try cairo-dock its very similar to awn but with fewer dependancies.

---

### Post by xXxBlender3DxXx on 2010-08-08
Thanks. I tried it (had like 5 dependencies), but it doesn't have some features that AWN has (I tried almost all of the docks).

I am going to try to see what dependencies I can fiddle...

---

### Post by fabounet on 2010-08-10
> it doesn't have some features that AWN has
did yuo try the latest versio n(2.2)
because I don't see what feature could miss in Cairo-Dock :-)

---

### Post by elliotn on 2010-08-10
I prefer AWN too

---

### Post by xXxBlender3DxXx on 2010-08-10
Well, I tried. It works, but it came with GDM... So much for a KDE-only desktop.

Compiling form source yields tons of errors. I had all of the dependencies, and I have had some experience with compiling, since LFS was one heck of a weekend ;)

Oh well, Gnome suits my needs, and I like it also.

---

### Post by linux18 on 2010-08-10
LFS FTW!
I really want to create a linux from scratch, but I've been so busy lately that I don't have a full weekend to to enjoy compiling from source :(

Oh well, remember to mark the thread as solved

---

