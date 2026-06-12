---
title: "Cannot find where things are going"
date: 2010-09-09
forum: General Help
---

### Post by thedoctor81877 on 2010-09-09
I just recently upgraded to Ubunutu beta 10.10, & now whenever I minimize anything, I cannot find where said program is going to. The programs do not appear anywhere, like before where they were on the bottom panel or whatever. Help please.

---

### Post by Dex73 on 2010-09-09
Have you deleted your window list by chance? Another idea my be it's going to another workspace, but no window list sounds more like it to me.

---

### Post by kerry_s on 2010-09-09
> **thedoctor81877 said:**
> I just recently upgraded to Ubunutu beta 10.10, & now whenever I minimize anything, I cannot find where said program is going to. The programs do not appear anywhere, like before where they were on the bottom panel or whatever. Help please.

if i remember right, use the workspace icon on the left, it should zoom all active apps.

---

### Post by thedoctor81877 on 2010-09-09
I do not see a workspace icon on the left. Also, I do not see any window list either. ?!?

---

### Post by thedoctor81877 on 2010-09-09
Part of the prob, at least I think, is that I have a netbook, but when I log on now (this was NOT happening in 9.04), the only choices I have for log-on options is Desktop Mode, not Netbook Remix. Please help.

---

### Post by garvinrick4 on 2010-09-10
> **thedoctor81877 said:**
> Part of the prob, at least I think, is that I have a netbook, but when I log on now (this was NOT happening in 9.04), the only choices I have for log-on options is Desktop Mode, not Netbook Remix. Please help.

```
sudo apt-get install ubuntu-netbook
```

After installed go to System/Admin to Login Screen and can go back and forth between gnome desktop and netbook-remix.

---

### Post by garvinrick4 on 2010-09-10
```
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

### Post by kerry_s on 2010-09-10
you guys do realize were talking 10.10 beta here.

you do not have to install anything! netbook always comes with gnome already, you just log out & select it.


the workspace icon is the one that looks like it has 4 squares on it, pink & gray(silver) i think. it's just above the 3 black ones.

---

### Post by garvinrick4 on 2010-09-10
```
rick@rick-laptop:~$ uname -a
Linux rick-laptop 2.6.35-20-generic #29-Ubuntu SMP Fri Sep 3 14:55:28 UTC 2010 x86_64 GNU/Linux
rick@rick-laptop:~$ lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu maverick (development branch)
Release:    10.10
Codename:    maverick
rick@rick-laptop:~$ 
rick@rick-laptop:~$ aptitude show ubuntu-netbook
Package: ubuntu-netbook                  
State: not installed
Version: 2.032
Priority: optional
Section: metapackages
Maintainer: Ubuntu Desktop Developers <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, consolekit, cups, cups-bsd, cups-client,
         cups-driver-gutenprint, dc, desktop-file-utils, doc-base, eog, evince,
         file-roller, foomatic-db-compressed-ppds, foomatic-filters, gcalctool,
         gconf-editor, gdebi, gdm, gedit, genisoimage, ghostscript-x,
         gnome-about, gnome-applets, gnome-control-center, gnome-media,
         gnome-menus, gnome-nettool, gnome-panel, gnome-power-manager,
         gnome-session, gnome-session-canberra, gnome-system-monitor,
         gnome-system-tools, gnome-terminal, gnome-themes-selected,
         gnome-themes-ubuntu, gnome-utils, gstreamer0.10-alsa,
         gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio,
         gtk2-engines, gtk2-engines-pixbuf, gucharmap, humanity-icon-theme,
         indicator-applet-session, inputattach, language-selector,
         launchpad-integration, lftp, libgd2-xpm, libgnome2-perl,
         libpam-ck-connector, libsasl2-modules, libxp6, nautilus,
         nautilus-sendto, notify-osd, openprinting-ppds,
         plymouth-theme-ubuntu-logo, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-netbook-default-settings, ubuntu-sounds, unity,
         unzip, update-manager, update-notifier, wireless-tools, wpasupplicant,
         x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk, xkb-data, xorg,
         xscreensaver-data, xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, branding-ubuntu, brltty, brltty-x11, cheese,
            computer-janitor-gtk, empathy, espeak, evolution,
            evolution-exchange, evolution-indicator, evolution-plugins,
            evolution-webcal, example-content, firefox, firefox-gnome-support,
            foo2zjs, gnome-accessibility-themes, gnome-bluetooth,
            gnome-codec-install, gnome-disk-utility, gnome-mag, gnome-mahjongg,
            gnome-orca, gnome-screensaver, gnome-sudoku, gnome-user-guide,
            gvfs-fuse, gwibber, hplip, ibus, ibus-gtk, ibus-pinyin,
            ibus-pinyin-db-android, ibus-table, im-switch, indicator-appmenu,
            indicator-datetime, indicator-messages, jockey-gtk,
            kerneloops-daemon, laptop-detect, libnss-mdns, libpam-gnome-keyring,
            libunity-misc0, linux-headers-generic, min12xxw, mousetweaks,
            nautilus-share, network-manager-gnome, onboard, openoffice.org-calc,
            openoffice.org-gnome, openoffice.org-help-en-us,
            openoffice.org-impress, openoffice.org-style-human,
            openoffice.org-writer, pcmciautils, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox,
            rhythmbox-ubuntuone-music-store, shotwell, simple-scan,
            speech-dispatcher, splix, telepathy-idle, tomboy, totem,
            totem-mozilla, transmission-gtk, ttf-indic-fonts-core,
            ttf-kacst-one, ttf-khmeros-core, ttf-lao, ttf-liberation,
            ttf-punjabi-fonts, ttf-takao-pgothic, ttf-thai-tlwg,
            ttf-unfonts-core, ttf-wqy-microhei, ubufox, ubuntu-docs,
            ubuntuone-client-gnome, usb-creator-gtk, xcursor-themes, xdg-utils
Description: The Ubuntu Netbook system
 This package depends on all of the packages in the Ubuntu Netbook system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.
``` This is desktop if you download remix you get gnome with.
You download gnome desktop you have to install remix if you want it as a choice.

---

### Post by kerry_s on 2010-09-10
alright ;)

---

### Post by garvinrick4 on 2010-09-10
> **kerry_s said:**
> alright ;)
Sorry Kerry_s I am sitting here running 10.10 Desktop not remix. If you use remix install there is gnome/remix/remix 2d at install. You are quite right.

---

### Post by kerry_s on 2010-09-10
yeah, i was using unity 10.10, but it's so far from ready. i did use the gnome desktop for a while, but even that is still to crashy. i had so many bug reports(apport) popping up, it gave me windows flash backs. 

ohh no, i been infected by ubuntu. :lolflag:

---

