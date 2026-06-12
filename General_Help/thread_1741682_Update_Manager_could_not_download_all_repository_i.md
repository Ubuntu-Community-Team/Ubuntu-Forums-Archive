---
title: "Update Manager could not download all repository indexes"
date: 2011-04-28
forum: General Help
---

### Post by Hadeda on 2011-04-28
Hi,  I tried to download updates through the Update Manager and the following error occurred:    "Could not download all repository indexes ... The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.  Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out) Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Unable to connect to archive.canonical.com:http: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http: Some index files failed to download, they have been ignored, or old ones used instead."   ---  There is nothing wrong with my Internet connection. Everything else works perfectly fine.  Thank you!

---

### Post by cariboo on 2011-04-28
This question has nothing to do with security, Moved to General Help.

---

### Post by maniaq on 2011-04-29
they're just being hammered right now because 11.04 has been released - try it again - worked for me...

---

### Post by HDave on 2011-05-02
I switched to a local mirror server at a university near in (in software sources).  It helped A LOT!

---

