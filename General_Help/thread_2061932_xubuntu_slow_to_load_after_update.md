---
title: "xubuntu slow to load after update"
date: 2012-09-23
forum: General Help
---

### Post by supernater on 2012-09-23
I did a fresh install of xubuntu 12.04.  After the installation, I updated it and upon reboot xfce loaded slowly (over a minute).  I wasn't sure if I did something wrong so I reinstalled Xubuntu again and this time when I updated I only checked "Important Security Updates" and installed the updates.  This time xfce loaded quickly without any issues.  I went back to the update manager and checked "Recommended Updates" and installed the updates.  On reboot xfce loaded slowly indicating that the problem was with one of these packages.  I went to /var/log/apt/history.log and saw the following packages were installed....


Installed: 
printer-driver-postscript-hp 
libframe6 
libgeis1 
libgrail5

Upgraded: 
libsmbclient
libpolkit-backend-1-0
dmsetup
hdparm
gir1.2-dbusmenu-gtk-0.4
update-notifier-common
python-cupshelpers
libgutenprint2
gcalctool
fonts-liberation
vim-common
blueman
libldap-2.4-2
libgphoto2-l10n
base-files
libv4l-0
libcupsppdc1
libunity9
sysvinit-utils
libatspi2.0-0
update-notifier
libcupsimage2
libgphoto2-port0
libsane-hpaio
libcupscgi1
libgudev-1.0-0
system-config-printer-gnome
libglib2.0-data
at-spi2-core
oneconf
dconf-gsettings-backend
libjpeg-turbo8
libcairo-gobject2
smbclient
libcupsdriver1
zenity
glib-networking-common
liblaunchpad-integration-common
desktop-file-utils
pulseaudio
gstreamer0.10-alsa
liblaunchpad-integration-3.0-1
udisks
perl
libevince3-3
python-piston-mini-client
libcupsfilters1
xserver-xorg-core
gir1.2-dbusmenu-glib-0.4
libpython2.7
ghostscript-cups
libnm-util2
gstreamer0.10-plugins-base-apps
xserver-common
accountsservice
libgl1-mesa-dri
lightdm
libdevmapper1.02.1
libgnomevfs2-common
libutouch-geis1
libgnomevfs2-extra
foomatic-filters
python-software-properties
cups-client
libgl1-mesa-glx
gnome-sudoku
libpolkit-gobject-1-0
hplip
libxslt1.1
pulseaudio-module-x11
libwbclient0
perl-base
software-properties-common
libcairo2
libgs9-common
libgnutls26
perl-modules
xserver-xorg-input-vmmouse
printer-driver-gutenprint
libglapi-mesa
policykit-1
software-center
apport
psmisc
python2.7
gir1.2-gtk-3.0
shared-mime-info
grub-pc
libglib2.0-0
libv4lconvert0
libaccountsservice0
cups-ppdc
python-debtagshw
vim-tiny
update-manager
indicator-sound
update-manager-core
xkb-data
fontconfig
libgrip0
xserver-xorg-video-intel
linux-firmware
gnome-accessibility-themes
samba-common
python-gi
simple-scan
udev
python-aptdaemon
libgtk-3-bin
cups-common
sessioninstaller
network-manager
xserver-xorg-video-vmware
launchpad-integration
libhpmud0
ubuntu-sso-client-gtk
libcups2
gir1.2-unity-5.0
gdb
xserver-xorg-input-evdev
libdbusmenu-glib4
libnm-glib-vpn1
libgtk-3-0
printer-driver-ptouch
sudo
fontconfig-config
libgnomevfs2-0
python-problem-report
libnm-glib4
xfwm4
libdbusmenu-gtk4
system-config-printer-udev
libpulse-mainloop-glib0
cron
libdbusmenu-gtk3-4
software-properties-gtk
evince-common
gir1.2-atspi-2.0
libgcrypt11
ssl-cert
aptdaemon
libglib2.0-bin
libgail-3-0
libxatracker1
cups
libglade2-0
evince
libdevmapper-event1.02.1
policykit-1-gnome
python-gi-cairo
libasound2
ghostscript-x
python-ubuntu-sso-client
gstreamer0.10-gnomevfs
indicator-sound-gtk2
nautilus-data
ubuntu-sso-client
gstreamer0.10-x
libdconf0
liblvm2app2.2
grub-pc-bin
libgs9
gir1.2-gudev-1.0
cups-bsd
python-gobject
libgstreamer-plugins-base0.10-0
libperl5.14
libudev0
printer-driver-hpcups
jockey-common
zenity-common
ghostscript
python-gst0.10
python2.7-minimal
mahjongg
jockey-gtk
gir1.2-launchpad-integration-3.0
libpolkit-agent-1-0
libsasl2-2
ntpdate
libart-2.0-2
gnome-games-data
liblaunchpad-integration1
python-apport
libfontconfig1
aptdaemon-data
liblightdm-gobject-1-0
openssl
libpango1.0-0
libpulse0
resolvconf
libpulsedsp
python-aptdaemon.gtk3widgets
samba-common-bin
system-config-printer-common
grub-common
grub2-common
upstart
sysv-rc
libglu1-mesa
libcupsmime1
glib-networking-services
libjpeg-turbo-progs
dconf-service
pastebinit
apport-gtk
libnautilus-extension1a
libsasl2-modules
initscripts
gnome-icon-theme
cups-filters
libgtk-3-common
gstreamer0.10-plugins-base
xserver-xorg-input-synaptics
libsqlite3-0
pulseaudio-utils
libxkbfile1
libssl1.0.0
glib-networking
printer-driver-hpijs
hplip-data
gir1.2-pango-1.0
libgphoto2-2
gnomine


I have no idea where to go from here.  One of these updates is causing the problem.  How can I figure out which one it is?  Should I reinstall and only check "Important Security Updates"?

---

### Post by Toz on 2012-09-23
You may be experiencing the problem discussed in this thread: [http://ubuntuforums.org/showthread.php?t=1970326]("http://ubuntuforums.org/showthread.php?t=1970326").

Have a look at post #15 - there is a workaround. It would be interesting to know if the workaround works for you as well.

---

### Post by supernater on 2012-09-24
Looks like the bug is being tracked.

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/996791)

It looks like the fix involved the accounts-daemon and I can see from my printout that accountsservice was one of the packages updates.  Also, in the bug report one of the comments says...

```
after selecting only the Important security updates -- no login issue (date 09 Jun 12)
after selecting Recommended updates one by one i found the packages that cause the "slow" login issue:

glib-networking (Size: 52kB) version 2.32.1-ubuntu1
glib-networking-common (Size: 6kB) version 2.32.1-ubuntu1
glib-networking-services (Size: 13kB) version 2.32.1-ubuntu1

I have tested it on a 32bit and 64bit machine. It looks like only the 64bit is afected of this issue.
```

There are some other solutions in the comments but I'll have to weed through them until I find the one that works for me.  At least I know it's not my machine.

---

