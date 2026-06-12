---
title: "Why can I not update?"
date: 2010-09-29
forum: General Help
---

### Post by dollarside on 2010-09-29
One day when my Ubuntu 10.04 LTS was searching for updates, it couldn't and gave me these words:

Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg](http://linux.dropbox.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to linux.dropbox.com:80 (174.36.30.70). - connect (110: Connection timed out)
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://linux.dropbox.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to linux.dropbox.com:http:
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to linux.dropbox.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

How do I fix this?

---

### Post by s0rc3r3r on 2010-09-29
Are you sure that error message is not because of a drop in your Internet connection speed?

Cuz at times I used to get such messages when I try to update and mostly its because of severe drop in connection speed

---

### Post by Irony on 2010-09-29
It just means the dropbox repository (which is maintained by dropbox) is not available, personally I keep all my repositories unticked except the security ones.

---

