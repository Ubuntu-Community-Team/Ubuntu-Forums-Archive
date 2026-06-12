---
title: "crashed desktop, need help"
date: 2010-03-15
forum: General Help
---

### Post by saggitheman on 2010-03-15
i installed recordmydesktop trough terminal and it didn't have a start up icon so i started it through the terminal. and it started recording but all i saw was a white stripe in the bottom of  the screen, and i could not stop it. so i clicked on the force quit icon and pressed in the bottom of the screen, with was stupid. my desktop chrased and i don't have a background anymore, just black and i cannot right click on the desktop. 

How do i get this working again?

thanks in advanced

---

### Post by highspider on 2010-12-16
this will restart the desktop hope this works

sudo /etc/init.d/gdm restart

o-yeah 
I don't know how bad it is if you cant get a command prompt use
ctr+alt+f1           (this tty1 mode)

to get back to normal screen
ctr+alt+f7  or ctr+atl+f8   (think f7 is normal mines f8 )

REINSTALL
sudo apt-get install ubuntu-desktop

or one of the desktop packages

here is mine -----------------------Ubuntu 10.04 LTS - the Lucid Lynx-----------------
devil@hell:~$ apt-cache show gnome-desktop-environment

Package: gnome-desktop-environment
Priority: optional
Section: universe/gnome
Installed-Size: 44
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: meta-gnome2
Version: 1:2.28+1ubuntu3
Depends: gnome-core (= 1:2.28+1ubuntu3), alacarte (>= 0.12.4), brasero (>= 2.28 ), cheese (>= 2.28 ), deskbar-applet (>= 2.28 ), dmz-cursor-theme, ekiga (>= 3.2.5), empathy (>= 2.28 ), epiphany-browser (>= 2.28 ) | gnome-www-browser, evince (>= 2.28 ), evolution (>= 2.28 ), evolution-data-server (>= 2.28 ), fast-user-switch-applet (>= 2.24) | gdm (>= 2.26), file-roller (>= 2.28 ), gcalctool (>= 5.28 ), gconf-editor (>= 2.28 ), gdm (>= 2.20.9), gnome-backgrounds (>= 2.28 ), gnome-bluetooth (>= 2.28 ), gnome-about (>= 2.28 ), gnome-disk-utility (>= 2.28 ), gnome-keyring (>= 2.28 ), gnome-media (>= 2.28 ), gnome-netstatus-applet (>= 2.28 ), gnome-nettool (>= 2.28 ), gnome-screensaver (>= 2.28 ), gnome-system-monitor (>= 2.28 ), gnome-system-tools (>= 2.28 ), gnome-themes (>= 2.28 ), gnome-user-guide (>= 2.28 ), gnome-user-share (>= 2.28 ), gnome-utils (>= 2.28 ) gstreamer0.10-alsa (>= 0.10.25), gstreamer0.10-plugins-base (>= 0.10.25), gstreamer0.10-plugins-good (>= 0.10.16), gstreamer0.10-tools (>= 0.10.25), gtk2-engines (>= 1:2.18.4), gucharmap (>= 1:2.28 ), gvfs-backends (>= 1.4), gvfs-bin (>= 1.4), hamster-applet (>= 2.28 ), seahorse (>= 2.28 ), seahorse-plugins (>= 2.28 ), sound-juicer (>= 2.28 ), swfdec-gnome (>= 2.26), totem (>= 2.28 ), totem-plugins (>= 2.28 ), vinagre (>= 2.28 ) | grdc, vino (>= 2.28 ), zenity (>= 2.28 ), libgnome2-perl (>= 1.042), desktop-base, policykit-1-gnome, gksu
Recommends: gnome-accessibility, gnome-games (>= 1:2.28 )
Suggests: gnome-dbg
Conflicts: gstreamer0.10-gnomevfs
Filename: pool/universe/m/meta-gnome2/gnome-desktop-environment_2.28+1ubuntu3_i386.deb
Size: 2226
MD5sum: da6bdf547efe11f5ed1e95d283983c0f
SHA1: a15b9ac27fee86e7bde44cff04a2d4dee5207fbc
SHA256: b469f324270421a3bd0cc8d95731f213c9472c074725e7bf31a232b7425fd759
Description: The GNOME Desktop Environment
 This is the GNOME Desktop environment, an intuitive and attractive
 desktop.
 .
 This package depends on the standard set of applications that are part
 of the official GNOME release. It provides much of what is necessary
 for daily use of a personal computer, including web browsing, email,
 CD burning and ripping, encryption tools, audio and video playback,
 network and communication tools, document viewers, remote desktop
 utilities, and much more.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

---

