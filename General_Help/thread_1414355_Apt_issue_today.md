---
title: "Apt issue today"
date: 2010-02-23
forum: General Help
---

### Post by rteslow on 2010-02-23
Hey all.  Using Karmic 64bit server.  I went to update APT today and here is what I received:

```
Get:1 http://security.ubuntu.com karmic-security Release.gpg [7,781B]
Get:2 http://security.ubuntu.com karmic-security/main Translation-en_US [7,781B]
99% [2 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.b
zip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Get:3 http://security.ubuntu.com karmic-security/restricted Translation-en_US [7
,781B]
66% [3 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.b
zip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Get:4 http://security.ubuntu.com karmic-security/universe Translation-en_US [7,7
81B]
49% [4 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.b
zip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Get:5 http://security.ubuntu.com karmic-security/multiverse Translation-en_US [7
,781B]
39% [5 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.b
zip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Get:6 http://security.ubuntu.com karmic-security Release [7,781B]
Get:7 http://us.archive.ubuntu.com karmic Release.gpg [7,781B]
Err http://security.ubuntu.com karmic-security Release

Get:8 http://us.archive.ubuntu.com karmic/main Translation-en_US [7,781B]
49% [8 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a b
zip2 file.
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Get:9 http://us.archive.ubuntu.com karmic/restricted Translation-en_US [7,781B]
44% [9 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a b
zip2 file.
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Get:10 http://us.archive.ubuntu.com karmic/universe Translation-en_US [7,781B]
40% [10 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a
bzip2 file.
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Get:11 http://us.archive.ubuntu.com karmic/multiverse Translation-en_US [7,781B]
36% [11 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a
bzip2 file.
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Get:12 http://us.archive.ubuntu.com karmic-updates Release.gpg [7,781B]
Get:13 http://us.archive.ubuntu.com karmic-updates/main Translation-en_US [7,781
B]
38% [13 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a
bzip2 file.
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Get:14 http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
[7,781B]
35% [14 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a
bzip2 file.
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Get:15 http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US [7
,781B]
33% [15 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a
bzip2 file.
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Get:16 http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
[7,781B]
31% [16 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com]bzip2: (
stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Get:17 http://us.archive.ubuntu.com karmic Release [7,781B]
Err http://us.archive.ubuntu.com karmic Release

Get:18 http://us.archive.ubuntu.com karmic-updates Release [7,781B]
Err http://us.archive.ubuntu.com karmic-updates Release

Fetched 140kB in 3s (42.3kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not upd
ated and the previous index files will be used.GPG error: http://security.ubuntu
.com karmic-security Release: The following signatures were invalid: NODATA 1 NO
DATA 2

W: A error occurred during the signature verification. The repository is not upd
ated and the previous index files will be used.GPG error: http://us.archive.ubun
tu.com karmic Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not upd
ated and the previous index files will be used.GPG error: http://us.archive.ubun
tu.com karmic-updates Release: The following signatures were invalid: NODATA 1 N
ODATA 2

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Relea
se

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Rele
ase

W: Some index files failed to download, they have been ignored, or old ones used
 instead.

```Searching hasn't turned up any results.  Any opinions?


Thanks!

---

### Post by rteslow on 2010-02-23
Problem resolved.  It seems that DNS on the router was capturing and redirecting me to a website other than the update sites.  Once this was realized I changed the router's settings and things were back to normal.

Thanks!

---

