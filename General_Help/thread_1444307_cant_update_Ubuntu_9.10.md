---
title: "cant update Ubuntu 9.10"
date: 2010-04-01
forum: General Help
---

### Post by coriron on 2010-04-01
I cannot use apt-get to update my new install of 9.10. it is running on a vmware server. it has internet access.

i'm getting the following error.

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Connection failed
Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  Connection failed [IP: 91.189.88.37 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  Connection failed [IP: 194.169.254.10 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  Connection failed [IP: 194.169.254.10 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by ali98ir on 2010-04-03
I also have the same problem using Karmic 9.10. The Internet access is fine but it fails to fetch from repository (404). I haven't changed any setting but cannot update any file recently. It seems the repository has the required packages, but the OS cannot fetch them correctly.

---

