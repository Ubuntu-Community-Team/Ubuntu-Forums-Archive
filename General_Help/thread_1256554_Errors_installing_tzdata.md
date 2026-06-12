---
title: "Errors installing tzdata"
date: 2009-09-02
forum: General Help
---

### Post by pawnrocket on 2009-09-02
During Updates I get this error

```
Extracting templates from packages: 100%
Setting up tzdata (2009l-0ubuntu0.9.04) ...

Current default timezone: 'America/New_York'
Segmentation fault
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by pawnrocket on 2009-09-02
From [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/419100]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/419100")Launchpad

---

### Post by pawnrocket on 2009-09-02
bump

---

### Post by pawnrocket on 2009-09-02
Segmentation fault

---

### Post by pawnrocket on 2009-09-02
How long am I suppose to bump for?

---

### Post by dfpsfp on 2009-10-06
> **pawnrocket said:**
> During Updates I get this error

```
Extracting templates from packages: 100%
Setting up tzdata (2009l-0ubuntu0.9.04) ...

Current default timezone: 'America/New_York'
Segmentation fault
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was having the same error. Some people suggested changing the time zone would help. But it didn't work for me. At the end I realized it's my debconf package is corrupted somehow. I couldn't get it installed from synaptic so I downloaded the debian package from [http://packages.ubuntu.com/jaunty/all/debconf/download](http://packages.ubuntu.com/jaunty/all/debconf/download). Find your own version of debconf and try again. It worked for me. I could install tzdata after reinstalling debconf first.

---

