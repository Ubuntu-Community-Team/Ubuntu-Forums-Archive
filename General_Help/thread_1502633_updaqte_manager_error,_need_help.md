---
title: "updaqte manager error, need help"
date: 2010-06-05
forum: General Help
---

### Post by jarmore on 2010-06-05
I can't fix it ... here is output from "sudo apt-get update" starting from first error:

------------------------------------------------
[I]Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg
  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Err [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_CA
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages
  Unable to connect to archive.getdeb.net:http:
Fetched 3,786B in 21s (179B/s)
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_CA.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_CA.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]
-----------------------------------------------------

I'd appreciate any help.

---

### Post by colorlessprism on 2010-06-05
there has been something going on with the "getdeb" and "playdeb" pages they have been down for more than a week now.

---

### Post by captainron042 on 2010-06-08
Thanks for the info. I have the same problem and was starting to get pissed 'cause I thought something was broken.

---

### Post by jarmore on 2010-06-08
Yes .. thanks colorlessprism ... good to know not just me.

---

