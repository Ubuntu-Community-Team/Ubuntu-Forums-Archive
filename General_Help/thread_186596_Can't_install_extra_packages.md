---
title: "Can't install extra packages"
date: 2006-06-02
forum: General Help
---

### Post by ajc4000 on 2006-06-02
Hi all,

Firstly, sorry if this has come up before, I tried searching but didn't find anything that was overly similar.

I've got a fresh install of Dapper (moved from FC4 yesterday) but don't seem to be able to install any extra packages. 

My current /etc/apt/sources.list is:
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

although I've tried some others I've found on the Internet and they all produce the same result. 

When running sudo apt-get update I get the lots of 403 forbidden errors:
```
alex@alex-desktop:~$ sudo apt-get update
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://security.ubuntu.com dapper-security Release
Ign http://ca.archive.ubuntu.com dapper Release.gpg
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://ca.archive.ubuntu.com dapper-updates Release.gpg
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://ca.archive.ubuntu.com dapper Release
Ign http://ca.archive.ubuntu.com dapper-updates Release
Ign http://ca.archive.ubuntu.com dapper/main Packages
Ign http://ca.archive.ubuntu.com dapper/restricted Packages
Ign http://ca.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://ca.archive.ubuntu.com dapper/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-updates/main Packages
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-updates/main Sources
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Errhttp://ca.archive.ubuntu.com dapper/main Packages
  403 Forbidden [IP: 85.133.25.8 80]
Ign http://security.ubuntu.com dapper-security/restricted Sources
Errhttp://ca.archive.ubuntu.com dapper/restricted Packages
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://ca.archive.ubuntu.com dapper/main Sources
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://ca.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://ca.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://ca.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://ca.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://security.ubuntu.com dapper-security/main Packages
  403 Forbidden
Errhttp://ca.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden [IP: 85.133.25.8 80]
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  403 Forbidden
Errhttp://security.ubuntu.com dapper-security/main Sources
  403 Forbidden
Errhttp://security.ubuntu.com dapper-security/restricted Sources
  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  403 Forbidden
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  403 Forbidden [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

and when using apt-get install XX nothing actually gets installed. 

I've tried programs such as EasyUbuntu, and couple of other sources list from the Internet, but it doesn't make any difference. 

Is there an obvious mistake that I'm making? I'd have thought this stuff should be setup automatically.

---

### Post by swamytk on 2006-06-02
Look at my earlier tips on solving this.

[http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden](http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden)

---

### Post by ajc4000 on 2006-06-02
[QUOTE=swamytk]Look at my earlier tips on solving this.

[http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden](http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden)[/QUOTE]

Thanks for that. Fixed it no problem :D

---

### Post by Angafirith on 2006-06-02
[QUOTE=swamytk]Look at my earlier tips on solving this.

[http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden](http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden)[/QUOTE]
Thank you. You've just made my day; I was just about to try reinstalling Dapper for the fourth time.

---

### Post by soft@cbov.org on 2006-07-07
hi ... i solve this problem with edition of file /etc/apt/apt.conf and remove "http" from line
Adquire::http::Proxy "false";
or removing the original /etc/apt/apt.conf

[]os
Cristofer

---

