---
title: "update manager error"
date: 2011-04-13
forum: General Help
---

### Post by stephenstop on 2011-04-13
My update manager had this error,will not update

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz  504  Gateway Time-out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  504  Gateway Time-out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Sub-process gzip returned an error code (1)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Orin on 2011-04-22
Bump. (Same issue)

I've tried poking around with the /etc/apt/sources.list, added some repositories to it, then it just gave me a longer list of errors, so I removed everything that wasn't there to begin with, and started over...still with no luck.

```
W:Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)
, W:Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

Cheers.

---

