---
title: "Requires untrust packages fo installation"
date: 2011-03-25
forum: General Help
---

### Post by suresh_vandiyur on 2011-03-25
when i want to install some update or software in ubuntu 10.10 its display this massage

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
how can i solve this?

#sudo apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [31.4kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [13.4kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [649B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages [109kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages [53.5kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages [1,506B]
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release

Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main amd64 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted amd64 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe amd64 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse amd64 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse amd64 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 242kB in 12min 12s (330B/s)
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg) Could not connect to in.archive.ubuntu.com:80 (111.91.91.37), connection timed out

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release](http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz) Unable to connect to in.archive.ubuntu.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

I get like this how to fix this. please help me

---

