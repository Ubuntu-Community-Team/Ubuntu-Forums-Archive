---
title: "Lucid Update Errors"
date: 2010-05-29
forum: General Help
---

### Post by Ichido on 2010-05-29
Lucid Update errors:

The latsest one is:

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

Then there is:

Error: 31

Also:

Error: 25

---

### Post by Gh0stDog on 2010-05-29
Web site and archive are down *again* according to [All about Getdeb ]("http://blog.getdeb.net/")

Just uncheck getdeb temporaly in your sources list if it is an issue for you. I bet it will be up again soon ;-)

---

### Post by Ichido on 2010-06-11
> **Gh0stDog said:**
> Web site and archive are down *again* according to [All about Getdeb ]("http://blog.getdeb.net/")

Just uncheck getdeb temporaly in your sources list if it is an issue for you. I bet it will be up again soon ;-)

Thanks, it worked.

---

