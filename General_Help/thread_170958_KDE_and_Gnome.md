---
title: "KDE and Gnome"
date: 2006-05-05
forum: General Help
---

### Post by qrees on 2006-05-05
Hi. I have recently installed ubuntu, but I'd like to have both Gnome and KDE installed. When I use Synaptic to install KDE it says that I have to uninstall packages like: kadu (communicator, works fine in KDE), lyx, aspell, gnome-panel etc. I'm using this apps so what do i have to do to keep them?

---

### Post by kingmonkey on 2006-05-05
are you doing:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by aysiu on 2006-05-05
That's weird.

What does your sources.list look like?

---

### Post by qrees on 2006-05-05
These packages will be deleted:

```
  aspell-bin dbus-1 dbus-glib-1 evolution evolution-exchange gnome-applets
  gnome-applets-data gnome-panel kadu kadu-alsasound libhal-storage0
  libhal0 libmusicbrainz4 libnautilus-burn1 libqt3c102-mt
  libsigc++-1.2-5c102 lsb lyx lyx-common lyx-qt qt3-qtconfig xlibmesa-glu
```

And I'm using aptitude:
```
aptitude install kubuntu-desktop
```

Any ideas?

---

### Post by aysiu on 2006-05-05
Yeah, my idea is that you may have conflicting repositories...
That's the only thing I can think of.

---

### Post by qrees on 2006-05-05
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050129)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe

# deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

deb http://security.ubuntu.com/ubuntu/ hoary-security universe
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe

# deb http://www.kadu.net/download/binary/ubuntu/repo/ hoary main

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

deb http://security.ubuntu.com/ubuntu/ breezy-security universe
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse
deb http://archive.czessi.net/ubuntu breezy main universe preview

```

Bu I don't think that's the problem. I had the same problem with original sources.list file.

---

### Post by aysiu on 2006-05-05
You have a mix of Hoary and Breezy repositories.
You also have online *and* CD sources.

---

### Post by qrees on 2006-05-05
I have commented out conficting repositories but there is no change :(

---

### Post by aysiu on 2006-05-05
[QUOTE=qrees]I have commented out conficting repositories but there is no change :([/QUOTE] Try this. Copy and paste these commands into a terminal. ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list_old
sudo cp breezy.list /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install kubuntu-desktop
sudo aptitude install aspell-bin dbus-1 dbus-glib-1 evolution evolution-exchange gnome-applets gnome-applets-data gnome-panel kadu kadu-alsasound libhal-storage0 libhal0 libmusicbrainz4 libnautilus-burn1 libqt3c102-mt libsigc++-1.2-5c102 lsb lyx lyx-common lyx-qt qt3-qtconfig xlibmesa-glu
rm breezy.list
```

---

