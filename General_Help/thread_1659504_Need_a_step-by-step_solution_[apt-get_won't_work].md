---
title: "Need a step-by-step solution [apt-get won't work]"
date: 2011-01-04
forum: General Help
---

### Post by Ali Kante on 2011-01-04
Hi everybody!

I'm having problems using apt-get behind a proxy. I've read a lot of threads and I tried many things, but nothing actually helped me further.

[COLOR=Navy]What's the problem?[/COLOR]
In a ubuntu meerkat installation ```
Linux ubuntu 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
``` inside a VM (VM Ware Workstation) apt-get produces the following errors:

```

john@ubuntu:~$ sudo apt-get update
[sudo] password for john: 
Err http://vesta.informatik.rwth-aachen.de maverick Release.gpg
  Could not connect to vesta.informatik.rwth-aachen.de:80 (137.226.34.229). - connect (113: No route to host)
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/main Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/main Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/multiverse Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/multiverse Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/restricted Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/restricted Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/universe Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick/universe Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates Release.gpg
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/main Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/main Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/multiverse Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/multiverse Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/restricted Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/restricted Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/universe Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-updates/universe Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security Release.gpg
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/main Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/main Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/multiverse Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/multiverse Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/restricted Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/restricted Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/universe Translation-en
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/ maverick-security/universe Translation-en_US
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Ign http://vesta.informatik.rwth-aachen.de maverick Release
Ign http://vesta.informatik.rwth-aachen.de maverick-updates Release
Ign http://vesta.informatik.rwth-aachen.de maverick-security Release
Ign http://vesta.informatik.rwth-aachen.de maverick/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/multiverse i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/multiverse i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick/multiverse i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/restricted Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/main Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/multiverse Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/universe Sources
Ign http://vesta.informatik.rwth-aachen.de maverick-security/main i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/restricted i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/universe i386 Packages
Ign http://vesta.informatik.rwth-aachen.de maverick-security/multiverse i386 Packages
Err http://vesta.informatik.rwth-aachen.de maverick/main Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/restricted Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/multiverse Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/universe Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/main i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/restricted i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/universe i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick/multiverse i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/restricted Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/main Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/universe Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/main i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/restricted i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/universe i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-updates/multiverse i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/restricted Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/main Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/multiverse Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/universe Sources
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/main i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/restricted i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/universe i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://vesta.informatik.rwth-aachen.de maverick-security/multiverse i386 Packages
  Unable to connect to vesta.informatik.rwth-aachen.de:http:
Err http://extras.ubuntu.com maverick Release.gpg
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (113: No route to host)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
  Unable to connect to extras.ubuntu.com:http:
Ign http://extras.ubuntu.com maverick Release
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex
Ign http://extras.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com maverick/main Sources
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://extras.ubuntu.com maverick/main Sources
Ign http://extras.ubuntu.com maverick/main i386 Packages
Err http://extras.ubuntu.com maverick/main Sources
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com maverick/main i386 Packages
  Unable to connect to extras.ubuntu.com:http:
W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/Release.gpg  Could not connect to vesta.informatik.rwth-aachen.de:80 (137.226.34.229). - connect (113: No route to host)

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/Release.gpg  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (113: No route to host)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/Release.gpg  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/main/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/restricted/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/multiverse/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/universe/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/main/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/universe/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/restricted/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/main/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/universe/source/Sources.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://vesta.informatik.rwth-aachen.de/ftp/pub/Linux/ubuntu/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  Unable to connect to vesta.informatik.rwth-aachen.de:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to extras.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

```[COLOR=Navy]What works?[/COLOR]
Actually the access to the internet works. The VM is bridged and receiving a NAT address. I used the *System>Preferences>Network Proxy* to set the proxy values. I'm having access to the internet, this is actually posted right out of the VM. I've tried if wget runs. It does. It runs even with the IP address of the error message (137.226.34.229):

```

john@ubuntu:~$ wget 137.226.34.229
--2011-01-04 01:46:56--  http://137.226.34.229/
Resolving www.my-proxy.de... 114.13.131.230
Connecting to www.my-proxy.de|114.13.131.230|:8080... connected.
Proxy request sent, awaiting response... 200 OK
Length: 444 [text/html]
Saving to: `index.html.3'

100%[======================================>] 444         --.-K/s   in 0s      

2011-01-04 01:46:56 (34.5 MB/s) - `index.html.3' saved [444/444]

```I'm not a complete newbie, but I still have some problems figuring out, what to do when I'm stuck. So a step-by-step analysis or a way respectively would be great, so that I could participate and learn from it for any further problems in the future.

[COLOR=Navy]What I already did[/COLOR]:


[LIST]
[*]I checked /etc/resolv.conf
[/LIST]
[INDENT][INDENT]```
# Generated by NetworkManager
domain localdomain
search localdomain
nameserver 192.168.43.2

```But whenever I add an entry to the resolv.conf file, the NetworkManager erases the entry after a reboot and the file looks again like above.
[/INDENT][/INDENT]
[LIST]
[*]I changed the source in the Ubuntu Software Center to diverse sources without success.
[*]I entered the proxy into apt.conf:
[/LIST]
[INDENT][INDENT]```
john@ubuntu:~$ cat /etc/apt/apt.conf
Aquire::http::Proxy "http://www.my-proxy.de":8080;

```[/INDENT][/INDENT]
[LIST]
[*]A lot of other little things out of several threads but with the same result. :-k No success...
[/LIST]
So right now I'm really kind of frustrated, because I've tried a lot, but I'm out of ideas and hope. :confused:
Another hint could be, that everything works just fine, if I am connected via a different WLAN without any proxy settings at all.

Any suggestion and hints are pretty appreciated! :-)

---

### Post by piquat on 2011-01-04
> **Ali Kante said:**
> 

[COLOR=Navy]What I already did[/COLOR]:


[LIST]
[*]I checked /etc/resolv.conf
[/LIST]
[INDENT][INDENT]```
# Generated by NetworkManager
domain localdomain
search localdomain
nameserver 192.168.43.2

```But whenever I add an entry to the resolv.conf file, the NetworkManager erases the entry after a reboot and the file looks again like above.
[/INDENT][/INDENT] 
On this.... you need to set that in the connections properties.  Under IPv4 settings, change it to DHCP (addresses only).  The boxes to enter a nameserver will be available at that point.

---

### Post by Ali Kante on 2011-01-04
Okay, besides that this doesn't solve the problem, I can't change the settings right now, because of a well known bug: The authentifcation window after changing the settings won't go away. And I can't update because of the upper problem. :lolflag:

---

### Post by Ali Kante on 2011-01-04
Nobody? :frown:

---

### Post by KJ KJ KJ on 2011-01-04
I had a similar problem with linaro. If you're using apt-get inside a chroot jail and it can't see /etc/apt.conf, proxying doesn't work. It really made my head hurt because everything else I tried using proxies did work!

---

### Post by Ali Kante on 2011-01-05
Okay, I puzzled it out on my own by adding one line to apt.conf:

cat /etc/apt/apt.conf
Acquire::http::'proxy "http://www.my-proxy.de":8080;
Acquire::ftp::'proxy "http://www.my-proxy..de":8080;

PS: Please remove the "'". It's only there because : P would mutate to this: :P


That did the trick! ):P

---

