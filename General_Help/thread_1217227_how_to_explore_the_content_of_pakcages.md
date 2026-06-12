---
title: "how to explore the content of pakcages"
date: 2009-07-19
forum: General Help
---

### Post by beyossi on 2009-07-19
Hi,

sorry if the question is too trivial as I am newbie with ubuntu.

I am trying to explore what modules each package contains, but with no much success.
Is there a generic way to explor them prior to installation?
for example, i want to know if it uses gtk+ or X, is there clutter inside or not, and etc...

example for packages i am talking about are:
- ubuntu-minimal
- lxde,gdm
- xubuntu-desktop
- ubuntu-desktop

---

### Post by sarfarazkazi on 2009-07-19
Go to System > Administration > Synaptic Package Manager, click on the package name and then click on the Properties button on the toolbar. You will get the requisite info.

---

### Post by Lampi on 2009-07-19
> **beyossi said:**
> I am trying to explore what modules each package contains, but with no much success.
You can browse the content of a package online as well @ [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by abhilashm86 on 2009-07-19
you can always find where the installed files are saved, use this command
```

whereis

```
example take gdm 
```

abhilash@abhilash:~$ whereis gdm
gdm: /usr/sbin/gdm /etc/gdm /usr/lib/gdm /usr/share/gdm /usr/share/man/man1/gdm.1.gz /usr/share/man/man8/gdm.8.gz
abhilash@abhilash:~$ 


```
after that use nautilus to browse files through terminal :) hope you got an idea??

---

### Post by 3rdalbum on 2009-07-19
> **beyossi said:**
> example for packages i am talking about are:
- ubuntu-minimal
- lxde,gdm
- xubuntu-desktop
- ubuntu-desktop

Except for gdm, they are all metapackages - they don't contain any files, they just pull in dependencies. Considering that you want to find out about the package contents BEFORE installing, you should look at the Dependencies for the package in Synaptic, or mark it for installation and have a look at the full list of what gets pulled in with it.

I also find that the "Dependent Packages" (reverse-dependencies) also gives me a clue as to what the package does and what it contains.

---

### Post by credobyte on 2009-07-19
```
sudo apt-cache show audacious

```

Would show you something similar to :
```
dainis@ubuntu:~$ sudo apt-cache show audacious
Package: audacious
Priority: optional
Section: universe/sound
Installed-Size: 3868
Maintainer: Ubuntu MOTU <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian Audacious Packagers <pkg-audacious-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 1.5.1-4ubuntu3
Depends: libatk1.0-0 (>= 1.20.0), libaudclient1 (= 1.5.1-4ubuntu3), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.15.0), libice6 (>= 1:1.0.0), libmcs1, libmowgli1 (>= 0.5.0), libpango1.0-0 (>= 1.22.0), libsamplerate0, libsm6, libx11-6, zlib1g (>= 1:1.1.4), audacious-plugins (>= 1.5.1), audacious-plugins (<< 2.0~), dbus, libaudid3tag1 (= 1.5.1-4ubuntu3), gtk2-engines-pixbuf
Recommends: audacious-plugins-extra (>= 1.5.1), audacious-plugins-extra (<< 2.0~), unzip, python-chardet
Conflicts: audacious--crossfade (<= 0.3.14-1build1)
Filename: pool/universe/a/audacious/audacious_1.5.1-4ubuntu3_i386.deb
Size: 1166504
MD5sum: 682b527d99b6af8dc72b3e95e3be990e
SHA1: 6ac755b49743c6df3b465cc4baed276797b5881a
SHA256: afbb104851b1b2a4692fcf5c017841729490fe556f55c0d6fa6112401c9ddbcb
Description: small and fast audio player which supports lots of formats
 Audacious is a fork of beep-media-player which supports winamp skins
 and many codecs.
 .
 In the default install, the following codecs are supported:
 .
  * MP3
  * Ogg Vorbis
  * AAC and AAC+
  * FLAC
  * Windows Media (WMA)
  * Musepack
  * TTA
  * Many module formats and much more!
 .
 Additionally, Audacious is extendable through plugins, and contains
 other useful features like LIRC support and support for last.fm.
 .
 This package contains the core player and its localization.
Homepage: http://www.audacious-media-player.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

