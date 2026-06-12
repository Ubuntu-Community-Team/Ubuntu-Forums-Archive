---
title: "Trying to install GUI on 9.04 server"
date: 2009-08-31
forum: General Help
---

### Post by Phixion on 2009-08-31
My sources.list

```

#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb ftp://mir1.ovh.net/ubuntu/ jaunty main restricted
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates main restricted
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb ftp://mir1.ovh.net/ubuntu/ jaunty universe
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty universe
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates universe
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb ftp://mir1.ovh.net/ubuntu/ jaunty multiverse
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty multiverse
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates multiverse
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb ftp://mir1.ovh.net/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

When I try to install ubuntu-desktop:

```

mark@ns204415:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: cups but it is not going to be installed
                  Depends: cups-driver-gutenprint but it is not going to be installed
                  Depends: fast-user-switch-applet but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gstreamer0.10-pulseaudio but it is not going to be installed
                  Depends: hwtest-gtk but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: pulseaudio but it is not going to be installed
                  Depends: pulseaudio-esound-compat but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: system-config-printer-gnome but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  Recommends: deskbar-applet but it is not going to be installed
                  Recommends: firefox
                  Recommends: firefox-gnome-support but it is not going to be installed
                  Recommends: foomatic-db-hpijs but it is not going to be installed
                  Recommends: gimp but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-user-guide but it is not going to be installed
                  Recommends: hal-cups-utils but it is not going to be installed
                  Recommends: hplip but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: libdeskbar-tracker but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: pidgin but it is not going to be installed
                  Recommends: pidgin-otr but it is not going to be installed
                  Recommends: pulseaudio-module-gconf but it is not going to be installed
                  Recommends: pulseaudio-module-hal but it is not going to be installed
                  Recommends: pulseaudio-module-x11 but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: tracker but it is not going to be installed
                  Recommends: tracker-search-tool but it is not going to be installed
                  Recommends: ubufox but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
                  Recommends: usb-creator but it is not going to be installed
E: Broken packages

```

Anyone have any idea what's going on? :/

---

### Post by zvacet on 2009-08-31
```
sudo apt-get -f install
```

---

