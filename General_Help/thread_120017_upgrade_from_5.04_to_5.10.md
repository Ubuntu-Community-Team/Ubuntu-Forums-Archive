---
title: "upgrade from 5.04 to 5.10"
date: 2006-01-20
forum: General Help
---

### Post by wmoon on 2006-01-20
i changed the synaptic sites to breezy and marked and applied upgrades. the install started and seemed to freeze after the teminal said..... /tmp/tmpuKrW3U.

please help.....anyone out there?

---

### Post by earobinson on 2006-01-20
in the terminal type sudo apt-get dist-upgrade

(upgrade the distro uses dist-upgrade, a normal update used upgrade) (not sure how synaptic handles this)

---

### Post by wmoon on 2006-01-20
A similar result as follows appeared in the terminal:


ppp (2.4.3-20041231+3) unstable; urgency=medium

  * Removed patch 057_pppoe-interface-change which was refused
by the
    upstream maintainer. Now users must arrange for the ethernet
    interface used for PPPoE to be up.
  * The PPPoA plugin does not require anymore the libatm1
package to be
    installed.

 -- Marco d'Itri <md@linux.it>  Sun, 20 Feb 2005 20:34:00 +0100
vim (1:6.3-068+4) unstable; urgency=medium

  * The kvim patch is unmaintained and has some annoying bugs,
so we decided
    to remove the kvim packages from Debian.

 -- Norbert Tretkowski <nobse@debian.org>  Wed, 30 Mar 2005
13:39:52 +0200
alsa-base (1.0.9b-3) unstable; urgency=low

  As of this release, /etc/init.d/alsa no longer stores or
restores
  mixer levels. The /etc/init.d/alsa-utils init script now
performs
  that function.

 -- Jordi Mallach <jordi@debian.org>  Wed, 10 Jul 2005
15:00:00 +0200

/tmp/tmp2DXiFa

---

### Post by earobinson on 2006-01-20
can you post your /etc/fstab for us

---

### Post by wmoon on 2006-01-20
this is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by earobinson on 2006-01-20
lol sorry I was being stupid can you post your /etc/apt/sources.list

---

### Post by az on 2006-01-20
[QUOTE=wmoon]i changed the synaptic sites to breezy and marked and applied upgrades. the install started and seemed to freeze after the teminal said..... /tmp/tmpuKrW3U.

please help.....anyone out there?[/QUOTE]
That is not supposed to happen.  Perhaps this is a hardware problem?

Boot into recovery mode and type

apt-get -f install

Answer yes to any question you get.

If thet exits without any problem, try the dist-upgrade again.

apt-get dist-upgrade

---

### Post by wmoon on 2006-01-23
Here are /etc/asp/sources.list


deb [http://ubuntu.secs.oakland.edu](http://ubuntu.secs.oakland.edu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) brezzy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

