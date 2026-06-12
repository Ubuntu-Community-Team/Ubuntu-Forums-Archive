---
title: "Uninstalled python...now no graphics..."
date: 2010-01-17
forum: General Help
---

### Post by LumbeeNDN on 2010-01-17
...hey Guys, well, heres my story. I'm using Ubuntu 9.10. New user...did the install about a week ago on my Dell 610 lattitude. I did an uninstall of python 2.6, and about half way through the uninstall it just pops to a TTY login screen, and I couldn't get back to the GUI. After a reboot I get a message saying "Ubuntu is running in low-graphics mode"...error encountered..."(EE)Failed to load module "i810" (module does not exsist, 0)". So when I click OK I get 4 options:

>Run Ubuntu in low graphics mode...
>Reconfigure Graphics
>Troubleshoot error
>Exit to console

...tried all of these, and none seems to solve the problem. If I try the first option, I get a blank screen and nothing seems to happening, so I'm thinking it is loading the wrong graphics card. Not sure what to try next...and help appreciated..

---

### Post by John Bean on 2010-01-17
My suggestion is to do a new, clean Ubuntu install... and this time don't uninstall Python.

---

### Post by gradinaruvasile on 2010-01-17
Have you looked at the stuff that went along with python? 
Python is at the basis of most of Gnome packages AFAIK. You uninstalled a whole lot of other stuff too that depended on python.

I did a simulation on my Xubntu 9.10 and here is the list of packages that would go if i uninstall the python package:

```
The following packages will be REMOVED:
  aisleriot alsa-oss alsa-tools alsa-utils anjuta apport apport-gtk
  apport-hooks-medibuntu apt-xapian-index apturl apturl-common asoundconf-gtk
  audacious audacious-plugins audacious-plugins-extra audacity blueman
  bluez-btsco brasero byobu cairo-dock cairo-dock-plug-ins catfish cheese
  command-not-found deluge deluge-common deluge-gtk devhelp-common eog
  esound-clients evince exaile ffmpeg file-roller firefox firefox-3.5
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support
  galternatives gcalctool gconf-editor gconf2 gdb gdebi gdebi-core gdm gksu
  glchess glines gmountiso gnect gnibbles gnobots2 gnome-app-install
  gnome-blackjack gnome-codec-install gnome-doc-utils gnome-games
  gnome-keyring gnome-mahjongg gnome-media gnome-media-common gnome-menus
  gnome-mount gnome-netstatus-applet gnome-screensaver gnome-session-bin
  gnome-sudoku gnome-system-monitor gnome-system-tools gnome-user-guide
  gnome-user-guide-en gnometris gnomine gnote gnotravex gnotski gnumeric
  gpointing-device-settings gstreamer0.10-alsa gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good gtali
  gucharmap gwget gyachi hpijs hplip hplip-data iagno iaxcomm jockey-common
  jockey-gtk language-selector language-selector-common launchpad-integration
  libasound2 libasound2-dev libasound2-plugins libavdevice52 libbonoboui2-0
  libbonoboui2-dev libcanberra-gtk-module libcanberra-gtk0 libcanberra0
  libccc-0.1-dev libdevhelp-1-0 libebook1.2-dev libedataserver1.2-dev
  libesd-alsa0 libesd0-dev libfluidsynth1 libgconf2-dev libgegl-0.0-0
  libgksu2-0 libgladeui-1-9 libgnome-media0 libgnome2-0 libgnome2-common
  libgnome2-dev libgnome2-perl libgnome2-vfs-perl libgnomekbd-common
  libgnomekbd4 libgnomekbdui4 libgnomemm-2.6-1c2 libgnomeui-0 libgnomeui-dev
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgnomevfs2-extra
  libgstfarsight0.10-0 libiaxclient1 libjack0 libmjpegtools-1.9
  libpanel-applet2-0 libpanelappletmm-2.6-1c2 libportaudio2 libpurple-bin
  libpurple0 libpython2.6 librsvg2-bin libsdl-image1.2 libsdl-mixer1.2
  libsdl-ttf2.0-0 libsdl1.2-dev libsdl1.2debian libsdl1.2debian-alsa libsmpeg0
  libswfdec-0.8-0 libvisual-0.4-plugins libwxgtk2.6-0 libxine1
  libxine1-misc-plugins libxine1-x lsb-release mplayer mplayer-nogui mypaint
  network-manager-openvpn notification-daemon onboard openssl-blacklist
  openvpn openvpn-blacklist padevchooser paprefs pavucontrol pidgin
  pidgin-libnotify pidgin-otr policykit-gnome pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-module-zeroconf
  pyneighborhood pysdm python python-apport python-apt python-cairo
  python-cddb python-central python-chardet python-configglue python-cups
  python-cupshelpers python-dbus python-debian python-dev python-gconf
  python-gdbm python-glade2 python-gmenu python-gnome2 python-gnomecanvas
  python-gnomekeyring python-gnupginterface python-gobject python-gobject-dev
  python-gst0.10 python-gtk2 python-gtk2-dev python-gtk2-doc python-gtkhtml2
  python-httplib2 python-imaging python-launchpad-integration
  python-launchpadlib python-lazr-restfulclient python-lazr-uri
  python-libtorrent python-libxml2 python-mmkeys python-mutagen python-newt
  python-notify python-numpy python-oauth python-openssl python-pam
  python-pkg-resources python-problem-report python-protobuf python-pygame
  python-pyinotify python-pyorbit python-rdflib python-serial python-sexy
  python-simplejson python-smbc python-software-properties python-support
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone-client python-ubuntuone-storageprotocol
  python-urwid python-virtkey python-vte python-wadllib python-xapian
  python-xdg python-xkit python-zope.interface python2.6 python2.6-dev qutecom
  rdesktop remmina remmina-xfce same-gnome sensors-applet
  sflphone-client-gnome sflphone-common sip-communicator skype
  software-properties-gtk sun-java6-plugin swfdec-gnome
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev totem totem-common totem-gstreamer totem-mozilla
  totem-plugins ubufox ubuntu-minimal ubuntuone-client ubuntuone-client-gnome
  ufw unattended-upgrades update-manager update-manager-core update-notifier
  update-notifier-common usb-creator usb-creator-common usb-creator-gtk
  vinagre virtualbox-3.1 vlc vlc-nox vlc-plugin-pulse wicd wine1.2 xawtv xchat
  xchat-common xfce4-xfapplet-plugin xfswitch-plugin xine-ui xsplash
  xubuntu-default-settings xubuntu-desktop xubuntu-gdm-theme xulrunner-1.9.1
  xulrunner-1.9.1-gnome-support xvidcap yelp youtube-dl
```

314 packages - and a whole lot more will be left useless. On the standard Ubuntu it should be even more.

Be more cautious when removing software - look at the list that is given to you by Synaptic or apt-get - if its long and has different package names on it, do not continue.


I suggest you reinstall your system if someone here hasnt got a better idea.

---

### Post by LumbeeNDN on 2010-01-17
```
sudo apt-get install ubuntu-desktop python
```
...this worked for me...props to [n0dix]("http://ubuntuforums.org/member.php?u=226577") for the fix.

John Bean...u have a budding future in technical support...Microsoft maybe?

grad...I hear you on watching whats being uninstalled...lesson learned...

---

### Post by John Bean on 2010-01-17
> **LumbeeNDN said:**
> [CODE]John Bean...u have a budding future in technical support...Microsoft maybe?

Most amusing, but don't give up the day job... which I sincerely hope doesn't in your case involve maintaining computer systems ;-)

---

### Post by zeroseven0183 on 2010-02-19
I have the same problem. Messed it up again.. sorry. I was trying to install Python 3.1 and remove Python 2.6 and 2.5 from Ubuntu Software Center then suddenly the screen goes black and was forced to run Ubuntu in low graphics mode.

- Tried ```
sudo dpkg-reconfigure xserver-xorg
``` but didn't fix it.
- Tried booting to recovery mode and fix broken packages but didn't fix it.
- When I checked the /etc/X11, I only found Xorg.conf.failsafe (and other files) but not the Xorg.conf. Here's what it contains (I don't know if it's relevant)

> 
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


I'm running LiveCD and wouldn't want to reinstall Ubuntu all over again as much as possible.
Is there a way to recover?

---

### Post by LumbeeNDN on 2010-02-19
...did u try this? 
sudo apt-get install ubuntu-desktop python

---

### Post by rschmidt13 on 2012-03-23
I had the same problem but had to fix the network interface (eth0) first in order to do an "apt-get install". Adding these two lines in /etc/network/interfaces worked for me. 

auto eth0
iface eth0 inet dhcp

---

### Post by nothingspecial on 2012-03-23
Old thread.

Closed.

---

