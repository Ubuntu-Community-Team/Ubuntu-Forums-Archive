---
title: "installing unity in 10.04"
date: 2010-11-01
forum: General Help
---

### Post by blur xc on 2010-11-01
Hey, I just read [this]("http://www.ubuntugeek.com/how-to-install-unity-in-ubuntu-10-0410-10.html") over at Ubuntu Geek, but all I get is package not found.  What am I missing?

Thanks,
BM

---

### Post by garvinrick4 on 2010-11-01
What does:
```
aptitude show unity
```
does it show unity in 10.04, I am not running unity in 10.04 did
not no was possible. I am going over to 10.04 and check it out.

---

### Post by garvinrick4 on 2010-11-01
```
Was a package in 10.10 but not in 10.04 there was a ubuntu-netbook in 10.04 

rick@rick-laptop:~$ aptitude show unity
E: Unable to locate package unity

rick@rick-laptop:~$ aptitude show ubuntu-netbook
Package: ubuntu-netbook
State: not installed
Version: 2.025.1
Priority: optional
Section: metapackages
Maintainer: Ubuntu Mobile Developers <ubuntu-mobile@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, consolekit, cups, cups-bsd, cups-client,
         cups-driver-gutenprint, dc, desktop-file-utils, doc-base, eog, evince,
         file-roller, foomatic-db, foomatic-db-engine, foomatic-filters,
         gcalctool, gconf-editor, gdebi, gdm, gedit, genisoimage, ghostscript-x,
         gnome-about, gnome-applets, gnome-control-center, gnome-media,
         gnome-menus, gnome-nettool, gnome-panel, gnome-power-manager,
         gnome-session, gnome-session-canberra, gnome-system-monitor,
         gnome-system-tools, gnome-terminal, gnome-themes-selected,
         gnome-themes-ubuntu, gnome-utils, go-home-applet, gstreamer0.10-alsa,
         gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio,
         gtk2-engines, gtk2-engines-pixbuf, gucharmap, humanity-icon-theme,
         indicator-applet-session, inputattach, language-selector,
         launchpad-integration, lftp, libgd2-xpm, libgl1-mesa-glx,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libxp6, maximus,
         nautilus, nautilus-sendto, netbook-launcher, notify-osd,
         openprinting-ppds, plymouth-theme-ubuntu-logo, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-netbook-default-settings, ubuntu-sounds, unzip,
         update-manager, update-notifier, webfav, window-picker-applet,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xterm, yelp,
         zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, bogofilter, branding-ubuntu, brltty, brltty-x11,
            cdparanoia, cheese, computer-janitor-gtk, dvd+rw-tools, empathy,
            espeak, evolution, evolution-exchange, evolution-indicator,
            evolution-plugins, evolution-webcal, example-content, f-spot,
            firefox, firefox-gnome-support, foo2zjs, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gvfs-fuse, gwibber, hplip, ibus, ibus-gtk,
            ibus-m17n, ibus-table, im-switch, indicator-messages, jockey-gtk,
            kerneloops-daemon, laptop-detect, libgl1-mesa-dri, libnss-mdns,
            libpam-gnome-keyring, linux-headers-generic, min12xxw, mousetweaks,
            nautilus-share, network-manager-gnome, onboard, openoffice.org-calc,
            openoffice.org-gnome, openoffice.org-help-en-us,
            openoffice.org-impress, openoffice.org-style-human,
            openoffice.org-writer, pcmciautils, plymouth-x11,
            pm-utils-powersave-policy, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox,
            rhythmbox-ubuntuone-music-store, simple-scan, speech-dispatcher,
            splix, telepathy-idle, tomboy, totem, totem-mozilla,
            transmission-gtk, ttf-indic-fonts-core, ttf-kacst-one,
            ttf-khmeros-core, ttf-lao, ttf-liberation, ttf-punjabi-fonts,
            ttf-takao-pgothic, ttf-thai-tlwg, ttf-unfonts-core,
            ttf-wqy-microhei, ubufox, ubuntu-docs, ubuntuone-client-gnome,
            usb-creator-gtk, wodim, xcursor-themes, xdg-utils
Conflicts: ubuntu-netbook-remix (<= 2)
Provides: ubuntu-netbook-remix
Description: The Ubuntu Netbook system
 This package depends on all of the packages in the Ubuntu Netbook system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

rick@rick-laptop:~$ 

```

---

### Post by blur xc on 2010-11-03
So what does that all mean?  Is the article wrong in saying that the unity package is in the 10.04 repos?  Or do I have to install the whole netbook-remix to get it?  If it's the latter, I'll pass...  Not interested in installing all those packages for the sake of trying a new launcher thing (dunno what it is, exaclty).

Thanks,
BM

---

