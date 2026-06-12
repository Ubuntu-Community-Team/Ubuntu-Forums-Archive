---
title: "Applications most needed after a Ubuntu KDE minimal install..."
date: 2010-02-06
forum: General Help
---

### Post by gymophett on 2010-02-06
What are the applications most needed after an Ubuntu minimal install? 
 I have installed xorg and KDE-Minimal after doing a base minimal install.
 Now I need a network manager for my wireless networks, and I don't know what it is called.
 I also need to know the best package manager, everything I should need after doing an Ubuntu KDE minimal install.
 I also need an app where I can right click and extract a file.
 Any help would be appreciated. 
 Thank you! 

EDIT: I just realized how much had to be installed. PLEASE help.

---

### Post by ankspo71 on 2010-02-07
Hi,

network-manager-kde   = network manager
kpackagekit (or synaptic)  = package managers
ark       = kde file archiver
kate     = kde text editor
k3b      = kde cd burner
gdebi   = deb package installer
konsole = kde terminal

The dependencies of kubuntu-desktop:
```
Depends: alsa-base, alsa-utils, anacron, ark, bc, ca-certificates, cups, cups-bsd, cups-client, dc, dolphin, foomatic-db, foomatic-db-engine, foomatic-filters, genisoimage, ghostscript-x, hal, inputattach, kde-window-manager, kde-zeroconf, kdebase-workspace-bin, kdemultimedia-kio-plugins, kdepasswd, kdm, khelpcenter4, klipper, kmix, konsole, ksnapshot, ksysguard, ksystemlog, language-selector-qt, lftp, libgl1-mesa-glx, libpam-ck-connector, libsasl2-modules, libxp6, okular, openprinting-ppds, phonon-backend-xine, plasma-desktop, pnm2ppa, screen, smbclient, software-properties-kde, systemsettings, ttf-dejavu-core, ttf-freefont, unzip, wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs, xkb-data, xorg, zip
Recommends: acpi-support, akregator, amarok, apport-kde, apturl-kde, avahi-autoipd, avahi-daemon, bluez-cups, bluez-utils, bogofilter, brltty, cdparanoia, cdrdao, dragonplayer, dvd+rw-tools, foo2zjs, foomatic-db-gutenprint, gnupg-agent, gtk2-engines-qtcurve, gwenview, hpijs-ppds, hplip, ibus-qt4, ijsgutenprint, im-switch, install-package, jockey-kde, k3b, kaddressbook, kamera, kate, kcalc, kcm-gtk, kcm-touchpad, kde-icons-oxygen, kdebase-plasma, kdebluetooth, kdegraphics-strigi-plugins, kdepim-kresources, kdepim-runtime, kdepim-strigi-plugins, kdepim-wizards, kdesudo, kerneloops-daemon, kmag, kmail, kmousetool, knotes, konqueror, konqueror-nsplugins, konqueror-plugin-searchbar, kontact, kopete, korganizer, kpackagekit, kppp, krdc, krfb, ktimetracker, kubuntu-default-settings, kubuntu-docs, kubuntu-firefox-installer, kubuntu-konqueror-shortcuts, kubuntu-notification-helper, kvkbd, kwalletmanager, laptop-detect, libgl1-mesa-dri, libnss-mdns, libqca2-plugin-ossl, min12xxw, network-manager-kde, okular-extra-backends, openoffice.org-calc, openoffice.org-impress, openoffice.org-kde, openoffice.org-style-oxygen, openoffice.org-writer, oxygen-cursor-theme, pcmciautils, pinentry-qt4, plasma-widget-facebook, plasma-widget-googlecalendar, plasma-widget-kimpanel, plasma-widget-kubuntu-feedback, plasma-widget-message-indicator, plasma-widget-networkmanagement, plasma-widget-quickaccess, plasma-widgets-addons, pm-utils-powersave-policy, printer-applet, pxljr, quassel, rdesktop, splix, system-config-printer-kde, ttf-indic-fonts-core, ttf-kacst, ttf-lao, ttf-thai-tlwg, ttf-unfonts-core, ttf-vlgothic, ttf-wqy-microhei, usb-creator-kde, userconfig, wodim, xcursor-themes, xdg-utils
```You won't need all of those installed, but sometimes it's easier to look at a list of items to choose from.
Hope this helps.

---

