---
title: "Synaptec connection error"
date: 2006-05-05
forum: General Help
---

### Post by johnleonard on 2006-05-05
Hi

When I try to upgrade any software I get the following:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/)
Sources.gz: Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

Is this a problem with corrupted etc/apt/spurces list? If so can you send me a new one?

Many thanks

---

### Post by sYs^ on 2006-05-05
try removing gb. from your sources.list then apt-get update again. may it'll help :>

**_Edit:_** I think something is wrong with the dns resolving because your system thinks gb.archive.ubuntu.com and security.ubuntu.com is your local pc(127.0.0.1), interesting :>

---

### Post by johnleonard on 2006-05-05
removing gb seems to have no effect. Any idea what I can do about the DNS issue? - Thanks!

---

