---
title: "debootstrap fails"
date: 2010-01-26
forum: General Help
---

### Post by lievendp on 2010-01-26
Hello people,

I'm currently trying to debootstrap a ubuntu karmic system.
The host is debian lenny.

First, lenny didn't have the debootstrap scripts for ubuntu so I downloaded the debootstrap package, extracted it and copied the scripts to the correct folder.

Now debootstrap seems to work, it's downloading files etc.
debootstrap --arch i386 karmic /data/debootstrapped/karmic/ [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
<lots of output>

Now I can chroot into the directory but nothing really works, I can't dpkg-reconfigure or apt-get or anything... (I can mount proc and sys but that should always be possible, right?)



This is the debootstrap.log:


Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5.0.0ubuntu7_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5.0.0ubuntu7_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.21_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you requested:
 base-passwd depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.21) ...

dpkg: base-files: dependency problems, but configuring anyway as you requested:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (5.0.0ubuntu7) ...

dpkg: regarding .../dpkg_1.15.4ubuntu2_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.8)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.4ubuntu2_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
dpkg: warning: ignoring pre-dependency problem!
dpkg: regarding .../dpkg_1.15.4ubuntu2_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 108 files and directories currently installed.)
Preparing to replace dpkg 1.15.4ubuntu2 (using .../dpkg_1.15.4ubuntu2_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you requested:
 dpkg depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
 dpkg depends on lzma; however:
  Package lzma is not installed.
Setting up dpkg (1.15.4ubuntu2) ...

Selecting previously deselected package libc6.
(Reading database ... 342 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.10.1-0ubuntu15_i386.deb) ...
dpkg: libc6: dependency problems, but configuring anyway as you requested:
 libc6 depends on libc-bin (= 2.10.1-0ubuntu15); however:
  Package libc-bin is not installed.
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
 libc6 depends on findutils (>= 4.4.0-2ubuntu2); however:
  Package findutils is not installed.
Setting up libc6 (2.10.1-0ubuntu15) ...

Selecting previously deselected package perl-base.
(Reading database ... 648 files and directories currently installed.)
Unpacking perl-base (from .../perl-base_5.10.0-24ubuntu4_i386.deb) ...
Setting up perl-base (5.10.0-24ubuntu4) ...
Selecting previously deselected package mawk.
(Reading database ... 1241 files and directories currently installed.)
Unpacking mawk (from .../mawk_1.3.3-15ubuntu1_i386.deb) ...
Setting up mawk (1.3.3-15ubuntu1) ...

Selecting previously deselected package debconf.
(Reading database ... 1260 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.5.27ubuntu2_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you requested:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.5.27ubuntu2) ...

/usr/share/debootstrap/scripts/karmic: line 149: repeatn: command not found
/usr/share/debootstrap/scripts/karmic: line 188: setup_available: command not found


Any idea on how to solve this? Awk is installed on the host system ofcourse.

thanks,
Lieven

---

