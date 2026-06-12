---
title: "ubuntu starts in terminal"
date: 2010-09-05
forum: General Help
---

### Post by udito on 2010-09-05
I have the following issue on my ubuntu 9.10 version:
[LIST]
[*]I start my linux machine
[*]after start-up is finished, I see the terminal.
[/LIST]
I have no clue how to access the GUI...

Any help regarding this?

Thanks, Udo

---

### Post by garvinrick4 on 2010-09-05
> **udito said:**
> I have the following issue on my ubuntu 9.10 version:
[LIST]
[*]I start my linux machine
[*]after start-up is finished, I see the terminal.
[/LIST]
I have no clue how to access the GUI...

Any help regarding this?

Thanks, Udo startx then enter

---

### Post by garvinrick4 on 2010-09-05
If that does not work ctrl/alt/F7

If that does not work:
```
sudo apt-get install ubuntu-desktop 
```

This is that package:
rick@rick-laptop:~$ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: installed
Automatically installed: no
Version: 1.197
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 61.4k
Depends: alacarte, alsa-base, alsa-utils, anacron, bc, ca-certificates,
         checkbox-gtk, cups, cups-bsd, cups-client, dc, desktop-file-utils,
         doc-base, eog, evince, file-roller, foomatic-db, foomatic-db-engine,
         foomatic-filters, gcalctool, gconf-editor, gdebi, gdm, gedit,
         genisoimage, ghostscript-x, gnome-about, gnome-applets,
         gnome-control-center, gnome-icon-theme, gnome-media, gnome-menus,
         gnome-nettool, gnome-panel, gnome-power-manager, gnome-session,
         gnome-session-canberra, gnome-system-monitor, gnome-system-tools,
         gnome-terminal, gnome-themes-selected, gnome-themes-ubuntu,
         gnome-utils, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps,
         gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap,
         indicator-applet-session, inputattach, language-selector,
         launchpad-integration, lftp, libgd2-xpm, libgl1-mesa-glx,
         libgnome2-perl, libpam-ck-connector, libsasl2-modules, libsdl1.2debian,
         libsdl1.2debian-pulseaudio, libxp6, metacity, nautilus,
         nautilus-sendto, notify-osd, openprinting-ppds, pnm2ppa, pulseaudio,
         pulseaudio-esound-compat, rarian-compat, screen,
         screensaver-default-images, seahorse, smbclient, software-center,
         software-properties-gtk, ssh-askpass-gnome, synaptic,
         system-config-printer-gnome, ttf-dejavu-core, ttf-freefont,
         ubuntu-artwork, ubuntu-sounds, unzip, update-manager, update-notifier,
         wireless-tools, wpasupplicant, x-ttcidfont-conf, xdg-user-dirs,
         xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl,
         xterm, yelp, zenity, zip
Recommends: acpi-support, aisleriot, app-install-data-partner, apport-gtk,
            avahi-autoipd, avahi-daemon, bluez, bluez-alsa, bluez-cups,
            bluez-gstreamer, bogofilter, branding-ubuntu, brasero, brltty,
            brltty-x11, cdparanoia, compiz, computer-janitor-gtk, dvd+rw-tools,
            empathy, espeak, evolution, evolution-couchdb, evolution-exchange,
            evolution-indicator, evolution-plugins, evolution-webcal,
            example-content, f-spot, firefox, firefox-gnome-support, foo2zjs,
            gbrainy, gcc, gdm-guest-session, gnome-accessibility-themes,
            gnome-bluetooth, gnome-codec-install, gnome-disk-utility, gnome-mag,
            gnome-mahjongg, gnome-orca, gnome-screensaver, gnome-sudoku,
            gnome-user-guide, gnomine, gvfs-fuse, hplip, ibus, ibus-gtk,
            ibus-m17n, ibus-table, im-switch, indicator-messages, jockey-gtk,
            kerneloops-daemon, laptop-detect, libgail-gnome-module,
            libgl1-mesa-dri, libnss-mdns, libpam-gnome-keyring, libwmf0.2-7-gtk,
            linux-headers-generic, make, min12xxw, mousetweaks, nautilus-share,
            network-manager-gnome, network-manager-pptp,
            network-manager-pptp-gnome, onboard, openoffice.org-calc,
            openoffice.org-gnome, openoffice.org-help-en-us,
            openoffice.org-impress, openoffice.org-math,
            openoffice.org-style-human, openoffice.org-writer, pcmciautils,
            pitivi, plymouth-theme-ubuntu-logo, plymouth-x11,
            pm-utils-powersave-policy, policykit-desktop-privileges,
            pulseaudio-module-bluetooth, pulseaudio-module-gconf,
            pulseaudio-module-x11, pxljr, quadrapassel, rhythmbox,
            rhythmbox-ubuntuone-music-store, simple-scan, speech-dispatcher,
            splix, telepathy-idle, tomboy, totem, totem-mozilla,
            transmission-gtk, tsclient, ttf-indic-fonts-core, ttf-kacst-one,
            ttf-khmeros-core, ttf-lao, ttf-liberation, ttf-punjabi-fonts,
            ttf-takao-pgothic, ttf-thai-tlwg, ttf-unfonts-core,
            ttf-wqy-microhei, ubufox, ubuntu-docs, ubuntuone-client-gnome,
            usb-creator-gtk, vinagre, vino, wodim, xcursor-themes, xdg-utils
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.

---

### Post by udito on 2010-09-05
that was fast rick :D

unfortunately nothing worked... :confused:

[LIST]
[*]**sudo startx**
[INDENT]Fatal server error:
Server is already active for display 0...[/INDENT]
[*]**ctrl/alt/F7**
[INDENT]Unfortunately produced no result...[/INDENT]
[*]**sudo apt-get install ubuntu-desktop**
[INDENT]ubuntu-desktop is already the newest version...[/INDENT]
[/LIST]

any clues what else to try?

---

### Post by garvinrick4 on 2010-09-05
> **udito said:**
> that was fast rick :D

unfortunately nothing worked... :confused:

[LIST]
[*]**sudo startx**[INDENT]Fatal server error:
Server is already active for display 0...[/INDENT]
[*]**ctrl/alt/F7**[INDENT]Unfortunately produced no result...[/INDENT]
[*]**sudo apt-get install ubuntu-desktop**[INDENT]ubuntu-desktop is already the newest version...[/INDENT]
[/LIST]

any clues what else to try?
```
sudo apt-get install gdm
```

---

### Post by udito on 2010-09-05
[LIST]
[*]**sudo apt-get install gdm**
[INDENT]gdm is already the newest version...[/INDENT]
[/LIST]
nope... unfortunately...

---

### Post by garvinrick4 on 2010-09-05
How about Ctrl/Alt/ F2  into another terminal then Ctrl/Alt/F7
Your machine believes it is already running a desktop.

So startx tells you its running already but ctrl/alt and F7 all at SAME TIME should give
you a desktop. And you are hitting function keys F7 on top of keyboard.

---

### Post by udito on 2010-09-05
Tried
[INDENT]**Ctrl+Alt+F2**[/INDENT]
and
[INDENT]**Ctrl+Alt+F7**[/INDENT]
unfortunately nothing changes...

I attached a screenshot of the situation.

---

### Post by _Jake_ on 2010-09-05
anyone suggested 

```
sudo gdm start
```

I used to use that command on my old Server 9.10 box.

---

### Post by garvinrick4 on 2010-09-05
> **udito said:**
> Tried[INDENT]**Ctrl+Alt+F2**[/INDENT]and[INDENT]**Ctrl+Alt+F7**[/INDENT]unfortunately nothing changes...

I attached a screenshot of the situation. It opens in a terminal emulation from the
GUI. Got me gave you all I got on subject, got to be something real simple.

---

### Post by udito on 2010-09-05
thanks guys, got it working! -> at least partially...

the solution is this (when gdm is already running, like in my case):
[LIST]
[*]**sudo stop gdm**
[*]enter username & password
[*]**startx**
[/LIST]

gnome looks good again...

but it looks like I have to run through this procedures every time I restart my machine. problem is not solved...

If somebody has a suggestion, I'm all ears ;)

---

### Post by garvinrick4 on 2010-09-05
What do you think about:
```
sudo apt-get remove gdm
```
```
sudo apt-get clean
```
```
sudo apt-get install gdm
```

This gets a fresh package from the repository instead of the one in your cache.

---

### Post by udito on 2010-09-06
sorry rick, tried it, but it does not work...

---

### Post by udito on 2010-10-16
was not able to fix this. had to reinstall... unfortunately.

Thanks for the help.

---

### Post by gabriel b on 2010-10-16
Why is this marked as solved?

This seems to be the same problem as I have:

[http://ubuntuforums.org/showthread.php?t=1597450](http://ubuntuforums.org/showthread.php?t=1597450)

---

