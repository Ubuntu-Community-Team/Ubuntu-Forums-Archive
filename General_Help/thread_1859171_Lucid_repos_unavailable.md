---
title: "Lucid repos unavailable?"
date: 2011-10-13
forum: General Help
---

### Post by cryptotheslow on 2011-10-13
Using Lucid, just trying to grab the latest updates using Update Manager and get this:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.
```

Also just trying to grab wakeonlan or etherwake using Synaptic throws up a "Warning - 
You are about to install software that can't be authenticated! ... etc..."

Can I take it this is just due to the servers being overloaded currently thanks to the 11.10 release?

Fine if so, I'll not bother troubleshooting any further and get them later, just want to make sure I've not managed to break my own machine :D

---

### Post by cryptotheslow on 2011-10-13
Answered my own question really - those urls aren't responding from another machine here nor from a VPS the other side of the Atlantic.

I'll just wait a while for the download frenzy to reduce :popcorn:

---

