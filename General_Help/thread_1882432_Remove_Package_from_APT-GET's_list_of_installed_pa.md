---
title: "Remove Package from APT-GET's list of installed packages..."
date: 2011-11-17
forum: General Help
---

### Post by gleepwurp on 2011-11-17
Hi,

I've installed zoneminder, and the configuration part of the package failed. That being said, I was able to manually fix the installation, but since the "configuration" failed as far as apt-get knows, it tries to reconfigure it each time I update my system.

Is there a way to remove "zoneminder" from the list of installed package so that apt-get stops trying to configure it? Mind you, I want to keep zoneminder, just remove it from Apt-get's list...

Thanks!

Yannick.

---

### Post by plucky on 2011-11-17
> **gleepwurp said:**
> Hi,

I've installed zoneminder, and the configuration part of the package failed. That being said, I was able to manually fix the installation, but since the "configuration" failed as far as apt-get knows, it tries to reconfigure it each time I update my system.

Is there a way to remove "zoneminder" from the list of installed package so that apt-get stops trying to configure it? Mind you, I want to keep zoneminder, just remove it from Apt-get's list...

Thanks!

Yannick.

You can look in the file /var/lib/dpkg/status for **zoneminder** and see what its installed status is.

If you are happy editing system files,always make a backup first ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
gksudo gedit /var/lib/dpkg/status
```

Search for **zoneminder** and see what its dpkg status is.

As I don't have zoneminder installed,as an example I have used gparted which gives ```
Package: gparted
Status: [color=green]install ok installed[/color]
Priority: optional
Section: gnome
Installed-Size: 4212
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.5.1-1ubuntu3
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.24.0), libgtk2.0-0 (>= 2.14.0), libgtkmm-2.4-1c2a (>= 1:2.20.0), libpangomm-1.4-1 (>= 2.26.0), libparted0debian1 (>= 2.2-1), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.4.0)
Recommends: gksu
Suggests: xfsprogs, reiserfsprogs, reiser4progs, jfsutils, ntfsprogs, dosfstools, yelp, kpartx, dmraid, dmsetup
Description: GNOME partition editor
 GParted uses libparted to detect and manipulate devices and partition
 tables while several (optional) filesystem tools provide support for
 filesystems not included in libparted.
Homepage: http://gparted.sourceforge.net
Original-Maintainer: Anibal Monsalve Salazar <anibal@debian.org>

```

Note the line in green

Good Luck

---

### Post by gleepwurp on 2011-11-17
Hi Plucky,

changed:

Status: install ok half-configured

to:

Status: install ok installed

and that fixed it...

Thanks!

Gleepwurp

---

