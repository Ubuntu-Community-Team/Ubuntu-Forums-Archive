---
title: "error while loading shared libraries"
date: 2006-03-19
forum: General Help
---

### Post by yellow beard on 2006-03-19
im trying to install thunderbird and some other programs but when ever i try to install them i get this error:

./mozilla-installer-bin: error while loading shared libraries: libstdc++.so.5: c annot open shared object file: No such file or directory

or if i try to configure

root@yellowbeard:/home/yellowbeard/xmms# ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnuoldld
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

i have no idea what im doing can some one give me some tips?

---

### Post by tuxcantfly on 2006-03-19
sudo apt-get install libstdc++5

should fix the problem.

By the way, why don't you just use Ubuntu's packaged version? Install with

sudo apt-get install mozilla-thunderbird

---

### Post by tuxcantfly on 2006-03-19
as for the cc part, you'll need gcc

sudo apt-get install gcc

---

### Post by yellow beard on 2006-03-19
ok im getting quite a few errors from package manager

[http://nz.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://nz.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'nz.archive.ubuntu.com'
[http://nz.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://nz.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Temporary failure resolving 'nz.archive.ubuntu.com'
[http://nz.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://nz.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Temporary failure resolving 'nz.archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Temporary failure resolving 'security.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://wine.sourceforge.net/apt/binary/Release.gpg:](http://wine.sourceforge.net/apt/binary/Release.gpg:) Temporary failure resolving 'wine.sourceforge.net'

---

### Post by tuxcantfly on 2006-03-21
Your package lists apparently don't work. Change them:

sudo gedit /etc/apt/sources.list

and add these lines:

deb [ftp://ftp.ubuntu.com/ubuntu](ftp://ftp.ubuntu.com/ubuntu) dapper main restricted universe multiverse

then:

sudo apt-get update

and try again. If the error messages annoy you, just get rid of those lines in /etc/apt/sources.list

---

