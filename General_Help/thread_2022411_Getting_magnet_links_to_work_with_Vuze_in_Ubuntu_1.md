---
title: "Getting magnet links to work with Vuze in Ubuntu 12.04"
date: 2012-07-10
forum: General Help
---

### Post by sienile on 2012-07-10
I've been trying for the last week to get magnet links to work with Vuze in Ubuntu 12.

I took the following steps (all done as root):

gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/vuze %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

Then I removed the magnet association from transmission-gtk.desktop and copied in the below vuze.desktop before updating the database like so:

update-desktop-database

Clicking on a magnet link opens vuze, but doesn't open the magnet link. Vuze doesn't even seem to receive the parameter. 

How do I get my magnet links to work???:confused:

**TECHNICAL INFO:**

**Browser:** Chromium
**Vuze version:** 4.7.0.2/4 az2 (installed at /_programs/vuze/)
**Ubuntu version:** 12.04 with Gnome Shell installed, using Gnome Classic shell

**Relevant config files:**

***/usr/bin/vuze***
Simlinks to /_programs/vuze/vuze

***/usr/share/applications/vuze.desktop***
[Desktop Entry]
Categories=Java;Network;FileTransfer;P2P
Comment[en_US]=Multimedia Bittorrent Client
Comment=Multimedia Bittorrent Client
Encoding=UTF-8
Exec=vuze %u
GenericName[en_US]=Multimedia Bittorrent Client
GenericName=Multimedia Bittorrent Client
Icon=vuze.png
MimeType=x-scheme-handler/magnet;application/x-bittorrent;
Name[en_US]=Vuze
Name=Vuze
Path=/_programs/vuze/
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

---

### Post by sienile on 2012-07-14
Never mind... I figured it out myself. I needed to be calling "azureus %U" instead of vuze.

---

### Post by agxryt on 2013-01-10
Can you explain how to do this for a noob? I'm a little confused.

---

