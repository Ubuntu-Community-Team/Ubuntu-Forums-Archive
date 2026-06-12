---
title: "Could not download all repository indexes (10.04)"
date: 2010-06-08
forum: General Help
---

### Post by gypsumwolf on 2010-06-08
My network connection is just fine. It worked flawlessly on my laptop.

> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

```
Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/i18n/Translation-en_US.bz2  Unable to connect to archive.getdeb.net:http:
Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-amd64/Packages.gz  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by _khAttAm_ on 2010-06-08
^seems like getdeb server problem. Nothing to worry about. This will be fixed when the getdeb server is up..

---

### Post by drpjkurian on 2010-06-09
Hi
Why cant you try another server. I mean mirrors.

---

### Post by _khAttAm_ on 2010-06-09
> **drpjkurian said:**
> Hi
Why cant you try another server. I mean mirrors.

Because there are no mirrors.. 

Confirmation on server down: [http://blog.getdeb.net/2010/05/web-site-and-archive-down-again.html](http://blog.getdeb.net/2010/05/web-site-and-archive-down-again.html)

---

