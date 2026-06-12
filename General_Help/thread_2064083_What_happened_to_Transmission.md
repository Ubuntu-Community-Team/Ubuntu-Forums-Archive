---
title: "What happened to Transmission?"
date: 2012-09-28
forum: General Help
---

### Post by kleinempfaenger on 2012-09-28
Hi, 
todays update uninstalled Transmission. 
Prompt: "Uninstall unneccesary packages?" Yes. Later wanted to start Transmission and it wasn't there any longer.

When I want to reinstall Synaptic and Software Center mention a conflict between packages:

transmission-gtk: Depends: libcurl3-gnutls (>= 7.16.2-1) pero 7.22.0-3ubuntu4 no está instalado
                  Depends: libgtk-3-0 (>= 3.0.0) pero 3.4.2-0ubuntu0.4 no está instalado
                  Depends: zlib1g (>= 1:1.1.4) pero 1:1.2.3.4.dfsg-3ubuntu4 no está instalado
                  Depends: transmission-common (= 2.51-0ubuntu1.1) pero 2.71-0ubuntu1~precise1 no está instalado

What happened?

Tahnks and greetings, kl

---

### Post by kleinempfaenger on 2012-09-28
Missing packages are installed and reinstalled, but installation of Transmission still fails.

---

### Post by snowpine on 2012-09-28
Usually things like this happen as a result of mixing unsupported software sources and/or not having your system fully up to date.

Can you please post the content of your software sources:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

And always a good idea to make sure your system is up to date:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And finally we can use the -f tag to fix broken:

```
sudo apt-get -f install
```

---

### Post by kleinempfaenger on 2012-09-28
cat /etc/apt/sources.list



# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by kleinempfaenger on 2012-09-28
ls /etc/apt/sources.list.d/


christoph-egger-unknown-horizons-precise.list       precise-partner.list.save
christoph-egger-unknown-horizons-precise.list.save  private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
gnome3-team-gnome3-precise.list                     private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
gnome3-team-gnome3-precise.list.save                private-ppa.launchpad.net_commercial-ppa-uploaders_vendetta-online_ubuntu.list
google-earth.list                                   private-ppa.launchpad.net_commercial-ppa-uploaders_vendetta-online_ubuntu.list.save
google-earth.list.save                              rye-ubuntuone-extras-precise.list
igorgomes-ppa-precise.list                          rye-ubuntuone-extras-precise.list.save
igorgomes-ppa-precise.list.save                     tualatrix-ppa-precise.list
playdeb.list                                        tualatrix-ppa-precise.list.save
playdeb.list.save                                   ubuntu-wine-ppa-precise.list
precise-partner.list                                ubuntu-wine-ppa-precise.list.save

---

### Post by kleinempfaenger on 2012-09-28
Update shows problems with launchpad/igorgomes repository:

W: Imposible obtener [http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Imposible obtener [http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/igorgomes/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar




In Synaptic I can't see that repository. How could I see, which packages are/were related to that repository and how could I delete it?

---

### Post by snowpine on 2012-09-28
I am not familiar with these unsupported 3rd-party repos; I recommend you contact their maintainers for assistance with these apps.

---

### Post by kleinempfaenger on 2012-09-28
Ok, this is solved.

Synaptic - Options - Repositories 

eliminated failing and some other 3rd-party  repositories. Afterwards installed Transmission without problems. 

Thanks snowblind

and greetings, kl

---

